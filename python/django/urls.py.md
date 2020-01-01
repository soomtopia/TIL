## urls.py

urls.py 분석하기

##### urls.py 란

사용자가 요청한 url 을 확인후 해당하는 view와 연결해주는 기능을 내용들을 작성한다.

settings.py 를 확인해보면 __ROOT_URLCONF = '<project_name>.urls'__이라고 되어있다.

```python
ROOT_URLCONF = 'happynewyear.urls'
```

내 프로젝트 이름이 happynewyear이 여서 저렇게 되어있는데, 실제로 해당 폴더에 urls.py가 존재한다.

urls.py

```python
"""happynewyear URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/2.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path, include


urlpatterns = [
    path('admin/', admin.site.urls),
]

```

default urls.py 를 확인해보면 이렇게 되어있다. 

보통 start-app 이후에 내부에 `urls.py` 를 만들어 준 후 root urls.py 에 include 해서 파일을 관리한다.

```python
# project urls.py
urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', include('blog.urls')),
]
```

#### path ( *route* , *view* , *kwargs = None* , *name = None* )

##### route 

문자열의 인수를 반환한다. `path('admin/<:a>/<:b>/<:c>')`과 같은 적어둔 형식으로 들어온 url과 매칭을 순차적으로 처리한다. `<:name>` 와 같이 꺽쇠로 들어온 값은 변수로 들어올 수 있다. default 는 문자열이나, 정수로 반환하고 싶은 경우라면 ` <int:sum>` 이런식으로 작성하면 된다. 

##### view

맵핑이된 route 를 해당하는 함수에 연결하는데, 해당 연결되는 함수를 명시해준다. views에 있는 함수를 명시할 땐 `views.<method_name>`  으로 작성하면 된다. 

##### kwargs

뷰 함수에 추가 인수를 전달해야할 경우 사용한다. 

##### name

url conf 에 이름을 지정할 수 있다. url 명명을 지정하면 편리한 경우가 많다.

> 찾아서 정리하기

##### regular expression

파이썬은 urls.py에 정규표현식을 사용한다.

```python
from . import views

urlpatterns = [
    path('articles/2003/', views.special_case_2003),
    path('articles/<int:year>/', views.year_archive),
    path('articles/<int:year>/<int:month>/', views.month_archive),
    path('articles/<int:year>/<int:month>/<slug:slug>/', views.article_detail),
]
```



#### re_path( *route* , *view* , *kwargs = None* , *name = None* )

path 와 동일하나, 정규표현식을 사용할 경우 사용하는 패턴. 

```python
from django.urls import include, re_path

urlpatterns = [
    re_path(r'^index/$', views.index, name='index'),
    re_path(r'^bio/(?P<username>\w+)/$', views.bio, name='bio'),
    re_path(r'^weblog/', include('blog.urls')),
    ...
]
```

routes 매개변수에 정규표현식을 쓴다

##### 정규표현식이란

문자열에 패턴 / 규칙 룰을 적용하는것. 이를 통해 문자열 검색을 편리하게 할 수 있다.

`from django.urls import re_path` 를 꼭 임포트하자.

글자패턴

- 1글자 패턴 : [] 를 써준다

  [] 안에는 들어가야할 글자를 써주면 된다. 

  ##### 숫자의경우

  [0123456789] or [0-9] or /d

  ##### 소문자/대문자

  [a-z] or [A-Z]

- 시작 : ^
- 끝: &
- 반복: {(반복할숫자)}

##### sample

휴대폰 번호 정규표현식 {6,7}  < 6 or 7

`[01][0156789]-[1-9][0-9]{6,7}`

#### 뜯어보기

` re_path(r'^bio/(?P<username>\w+)/$', views.bio, name='bio'),`

##### r

routes 앞에 r 을 써줬다. 이 이유는 \d 나 \w 같은 명령어로 숫자나 문자를 표현한다고 가정했을 때, 보통 escape 를 두번 써줘야한다. 그걸 방지하기위해 앞에 r 을 써주면 알아서 escape 를 \\ 개 처리해준다. 

##### (?P<>\w+)

정규표현을 쓰겠다는 표현. 괄호치고 앞에 (?P<변수이름>\w)을 적어준다. \w 처럼 문자로 들어왔는지 판단하고, 문자가 맞는지 판별해준다.

#### include()

다른 파일의 경로를 포함할 때 사용하는 모듈. 보통 app url_conf 를 app root url_conf 에 적용한다. 



##### 여러값을 받고 싶은경우

아래처럼 사용해보자

```python
re_path(r'^(?P<numbers>[\d/]+/)', views.my_sum)
```

정규표현식으로 [\d+]/ 이런식으로 사용해서 계속 받을 수 있다.