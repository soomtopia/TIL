# Django Rest Framework

찾아본 것 정리



## [Serializers](https://www.django-rest-framework.org/api-guide/serializers/#serializers)

쿼리셋 또는 모델 인스턴스 형태의 데이터를 json/xml 과 같은 데이터 타입으로 바꿔주는 기능을 말한다. 하나하나 반환된 데이터타입을 python native data 로 바꾼 후 json/xml 과 같은 데이터 타입으로 변환하는 과정을 거친다. 

#### serializer 선언하기

###### sample

```python
from datetime import datetime

class Comment(object):
    def __init__(self, email, content, created=None):
        self.email = email
        self.content = content
        self.created = created or datetime.now()

comment = Comment(email='leila@example.com', content='foo bar')
```

serializer

```python
from rest_framework import serializers

class CommentSerializer(serializers.Serializer):
    email = serializers.EmailField()
    content = serializers.CharField(max_length=200)
    created = serializers.DateTimeField()
```

serializer 를 통해 받은 값을 python native data (dictionary) 로 변경할 수 있다

```python
serializer = CommentSerializer(comment)
serializer.data
# {'email': 'leila@example.com', 'content': 'foo bar', 'created': '2016-01-27T15:17:10.375877'}
```

python data > json 변환

```python
from rest_framework.renderers import JSONRenderer

serializer = CommentSerializer(comment)
json = JSONRenderer().render(serializer.data)
json
# b'{"email":"leila@example.com","content":"foo bar","created":"2016-01-27T15:17:10.375877"}'
```

json > python data 변환

```python
import io
from rest_framework.parsers import JSONParser

stream = io.BytesIO(json) # json 을 입력받기
data = JSONParser().parse(stream) # jsonparser 를 통해 stream parsing 

serializer = CommentSerializer(data=data)
serializer.is_valid()
# True
serializer.validated_data # python data 반환 (dict)
# {'content': 'foo bar', 'email': 'leila@example.com', 'created': datetime.datetime(2012, 08, 22, 16, 20, 09, 822243)}
```



#### 인스턴스 저장하기

유효성 검증이 완료된 데이터를 객체 인스턴스로 만들기 위해 `create()` 또는 `update()` 메서드를 사용할 수 있다.

```python 
class CommentSerializer(serializers.Serializer):
    email = serializers.EmailField()
    content = serializers.CharField(max_length=200)
    created = serializers.DateTimeField()

    def create(self, validated_data):
        return Comment(**validated_data)

    def update(self, instance, validated_data):
        instance.email = validated_data.get('email', instance.email)
        instance.content = validated_data.get('content', instance.content)
        instance.created = validated_data.get('created', instance.created)
        return instance
```

django model 인스턴스가 모델에 해당하는 경우에는 데이터 베이스에 저장하게 할 수 있다

```python
    def create(self, validated_data):
        return Comment.objects.create(**validated_data)

    def update(self, instance, validated_data):
        instance.email = validated_data.get('email', instance.email)
        instance.content = validated_data.get('content', instance.content)
        instance.created = validated_data.get('created', instance.created)
        instance.save()
        return instance
```

json 으로 변환할때는 `.save` 호출을 통해 검증된 데이터 기반으로 객체 인스턴스를 반환한다

#### validation

역직렬화 할 때 `is_valid`  False 일 경우 데이터 유효성이 올바르지 못한것을 의미. `errors` 를 통해 에러 메세지를 확인할 수 있다.

```python
serializer = CommentSerializer(data={'email': 'foobar', 'content': 'baz'})
serializer.is_valid()
# False
serializer.errors
# {'email': ['Enter a valid e-mail address.'], 'created': ['This field is required.']}
```

오류가 날 경우에, `serializers.ValidationError` 예외를 발생시키는 선택적 `raise_exception` 플래그를 사용한다. 이 예외는 HTTP400 예외를 리턴시킨다

다른 유효성 검사를 하고 싶은 경우 하위 클래스에 validate() 를 오버라이딩 해서 추가할 수있다!

```python
from rest_framework import serializers

class EventSerializer(serializers.Serializer):
    description = serializers.CharField(max_length=100)
    start = serializers.DateTimeField()
    finish = serializers.DateTimeField()

    def validate(self, data):
        """
        Check that start is before finish.
        """
        if data['start'] > data['finish']:
            raise serializers.ValidationError("finish must occur after start")
        return data
```

따로 validators 를 포함할 수도 있는듯

```python
def multiple_of_ten(value):
    if value % 10 != 0:
        raise serializers.ValidationError('Not a multiple of ten')

class GameRecord(serializers.Serializer):
    score = IntegerField(validators=[multiple_of_ten])
    ...
```

안에 `Meta` 클래스를 사용하여 유효성 메서드를 재사용할 수도 있다



### ModelSerializer

Django model 관련 serializer 를 만들 경우 사용하는 클래스

ModelSerializer 는 자동으로 Model field 를 가져온다

__repr__ 로 확인 가능 