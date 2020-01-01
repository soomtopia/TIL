# Python

python 문법 정리 

# 자료형

## Numeric

숫자타입 

- int : 정수형
- float : 실수형



## String 

문자열타입.` ``, ""` 을 둘 다 사용할 수 있다.  값 / 순서는 변경되지 않는다. 

##### """"""

여러줄을 한번에 사용 가능. `\n` 이 들어간다. 

```python
>>> str1 = "hello"
>>> str2 = "world"
>>> str3 = """
... hello
... wotld
... not
... world
... """
>>> str3
'\nhello\nwotld\nnot\nworld\n'
```

##### Formatter

c 언어와 비슷한 formatter

```python
>>> 'today is %d' % (today)
'today is 22'
```

현대 방식의 formatter

```python
>>> today = 22
>>> 'today is %d' % (today)
'today is 22'
>>> 'my name is {}'.format(
... 'juju')
'my name is juju'
>>> '{} x {} = {}'.format(2, 3, 2*3)
'2 x 3 = 6'
>>> '{1} x {0} = {2}'.format(2, 3, 2*3)
'3 x 2 = 6'
```

##### Indexing

문장 중 위치 순서를 통해 문자를 하나 뽑을 수 있다. 문자의 시작은 0부터! [] 로 뽑는다

```python
>>> hlo = "hello, world"
>>> hlo[0]
'h'
>>> hlo[4]
'o'
>>> hlo[6]
' '
```

##### Slicing

문자열 내부의 값을 자를 수 있다. 값은 복사된다. 원본의 값은 변경 x

```python
>>> hlo[7:10]
'wor'
>>> hlo[7:]
'world'
>>> hlo[7:-1]
'worl'
>>> hlo[7:-2]
'wor'
```

##### split

String.split() 값을 잘라준다. default 는 공백. 옵션을 넣으려면 `()`  안에 넣어준다. 

```python
>>> fruit_str = '거봉 수박 포도 복숭아 망고 딸기'
>>> fruit_str.split()
['거봉', '수박', '포도', '복숭아', '망고', '딸기']
>>> 
```



## Boolean

참 / 거짓 자료형 `true/false`



## List

여러 값을 저장할 수 있는 자료형. `[]` 를 사용한다. 

```python
>>> list = [1,2,3,4,5,6,7,8,9,10]
>>> import random
>>> random.choice(list)
2
>>> random.choice(list)
1
>>> random.choice(list)
8
>>> random.choice(list)
5
>>> 
```

##### append()

리스트 값을 추가할 때 쓰는 함수 

```python 
>>> list.append("hi")
>>> list
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'hi']
```

##### del list_name[index]

리스트 값을 삭제할때 사용한다.

##### my_list[1:3]

리스트 값 중 부분 값을 가져올 때 사용한다. 



## Tuple

리스트와 같으나, 값을 변경할 수 없다. append 도 불가능. 

```python
# tuple
>>> list
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'hi']
>>> list[0] = "바꾸기"
>>> list
['바꾸기', 2, 3, 4, 5, 6, 7, 8, 9, 10, 'hi']
>>> list[1] = "rara"
# tuple
>>> my_tuple = (1,2,3,4,5)
>>> my_tuple[0]
1
>>> my_tuple[0] = 'haha'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```



## Dictionary

key / value 로 연결되어 있는 집합. `{'key' : 'value'}` 를 사용한다.

관련된 정보를 연관시킨다. `{key: value}`

```python
>>> my_dict                                       
{'h': 'k', 'jj': 'kk', '수': '민'}
>>> my_dict['h']
'k'
>>> my_dict['h'] = "에이치"
>>> my_dict
{'h': '에이치', 'jj': 'kk', '수': '민'}
```

##### .values

값을 하나씩 뽑아오는 메서드

##### .items

각각의 딕셔너리 안의 요소를 튜플로 변경해준다.



## Type 변환

```python
>>> int(5.0)
5
>>> float(5)
5.0
>>> my_int = 5
>>> str(my_int)
'5'
>>> my_str = "coding"
>>> list(my_str)
['c', 'o', 'd', 'i', 'n', 'g']

```



## Function

함수. 반복되는 코드에 이름을 붙혀 재호출 되게 만든 함수

```python
def hello_func(a):
    print("hello_world")
    return a**2
```

#### 여러 값 리턴

파이썬은 여러 값이 리턴이 된다. 리턴이 될때는 `tuple` 자료형으로 packing 해서 던져준다. 

여러 변수를 통해 받으면 바로 unpacking 을 통해 받을 수 있다.

```python
>>> def add_mul(n1, n2):
...     return n1+n2, n1 *n2
... 
>>> add_mul(1,2)
(3, 2)
>>> a, b = add_mul(1,2)
>>> 
>>> a
3
>>> b
2
```



## Comment

주석. 컴퓨터가 무시하는 메모 `#` 를 사용한다

```python
print("Hello world") # 안녕?
```



## For

반복문. 반복되는 작업을 처리

```python
>>> for i in my_list:
...     print(i)
... 
1
2
3
4
>>> 
```



## while

반복문. 반복되는 작업을 처리 

#### while

```python
count = 0 
while count < 3:
	print('횟수 {}'.format(count))
    count += 1
```



## 변수

데이터를 담는 공간. 다른 값을 담으면 값이 변한다. 

```python
>>> my_int = 3
```



## //

파이썬은 / 로 나누면 소숫점까지 나온다. `//` 로 나눠야 int 정수형의 몫이 나온다. 



## 조건문

#### if

조건을 만났을 때 실행한다. 

```python
>>> input_name = "aaa"
>>> if input_name == 'aaa':
...     print("만나서 반가워요")
... 
만나서 반가워요
```

#### if-else

```python
if order:
    expression
else:
```

#### if-elif-else

중간 조건 값을 지정하고 싶을 때 `elif:` 를 사용한다.

```python
>>> if input_name == 'b':
...     print('nono')
... elif input_name == 'aaa':
...     print('yes')
... else:
...     print("nono")
```



## Continue / break

#### continue

아래 명령을  실행하지 않고, 다시 __조건문__으로 돌아간다. 

#### break

아래 명령을 실행하지 않고 __반복문__을 종료한다. 



## 기본 제공 함수

#### print()

어떤 값을 넣었을 때 출력해주는 함수. 

##### print('', end='')

default 는 엔터가 기본으로 들어가는데, 끝에 값을 지정할 수 있다.

```python
>>> print('soomin', end='hahaha\n')
soominhahaha
```



#### input()

컴퓨터에게 사용자가 어떤 값을 입력할 수 있게 도와주는 함수.

idle 에서 input() 이후 엔터를 누르면 깜박거림. 입력을 기다린다. 

```python
>>> input()
hi
'hi'
>>> input('이름을 입력하세요')
이름을 입력하세요soomin
'soomin'
>>> age = input('당신의 나이는?')
당신의 나이는?22
>>> age
'22'
```



#### type()

변수의 타입을 알 수 있다. 



####range()

범위 함수. 숫자를 넣으면 `0 ~ N-1` 



#### in / not in() 

리스트 안에 값이 있는지 유무 

```python
>>> my_list = ['a','b','c']
>>> my_list = ['a','b','c','d','f','s','o','m','z']
>>> 'a' in my_list
True
>>> 
>>> 'x' in my_list
False
```



#### choice()

_random_ 함수

```python
>>> list = [1,2,3,4,5,6,7,8,9,10]
>>> import random
>>> random.choice(list)
2
```

_sample_ 함수. 여러개의 값을 중복 없이 뽑기 가능. 

```python
>>> my_list
['a', 'b', 'c', 'd', 'f', 's', 'o', 'm', 'z']
>>> import random
>>> random.sample(my_list,3)
['c', 'f', 'm']
>>> 
```



#### comprehension

반복문 한줄에 사용하기

```python
>>> numbers = range(1,10)
>>> odd_numbers = []
>>> for number in numbers:
...     if number %2 == 1:
...             odd_numbers.append(number)
... 
>>> odd_numbers
[1, 3, 5, 7, 9]

# comprehension
>>> [number for number in numbers if number %2 == 1]
[1, 3, 5, 7, 9]
>>> 
```



## TMI

#### tuple vs list 의 차이 

공통점

- 일련의 객체를 저장
- 타입에 상관없는 요소 저장
- 순서를 관리

```python
>>> my_list = [1, 2, 3]
>>> type(my_list)
<class 'list'>
>>> my_tuple = (1, 2, 3)
>>> type(my_tuple)
<class 'tuple'>
```

차이점

- tuple - immutable. 변경 불가
- 따라서 List 에만 `.append()` 메서드가 존재 

##### 어떻게 다르게 사용하는가 

List 

단일 type 만 사용. 리스트 요소가 몇 개인지 불분명한 상황에 사용

```python
>>> find_files("*.py")
["control.py", "config.py", "cmdline.py", "backward.py"]
```

Tuple 

요소를 정확히 알고 있을 때 사용. 주소 / 위도 / 경도 / 주소같은 내용을 담을 때 사용한다. 따라서 위치가 튜플에서 정말 중요해진다.

```python
>>> denver = (44, "Denver", "CO", 40, 105)
>>> denver[1]
'Denver'
```



## namedtuple

튜플의 위치가 중요하기 때문에, 일련의 위치의 의미를 명시적으로 사용할 때 사용한다.

```python
>>> from collections import namedtuple
>>> Station = namedtuple("Station", "id, city, state, lat, long")
>>> denver = Station(44, "Denver", "CO", 40, 105)
>>> denver
Station(id=44, city='Denver', state='CO', lat=40, long=105)
>>> denver.city
'Denver'
>>> denver[1]
'Denver'
```



## package

> django 모듈 뜯어보다 공부

모듈들을 묶어 관리하는 더 큰 디렉토리를 패키지라한다. 패키지를 만들기 위해 필요한 구조들을 알아보자

##### `__init__.py`

패키지를 초기화 하는 역할. python 3.3 이후의 버전에서는 __init__.py를 생략할 수 있다. 하지만 하위 버전의 호환성을 위해 __init__.py 파일을 남겨두는 것이 좋다. (내용이 없어도 됨)



## Module

공통적인 함수 / 변수  / 클래스를 모아 놓은 `.py` 파일. 재사용이 가능하다는 장점이 있다

##### 모듈 예시 

```python
# mod1.py
def add(a, b):
    return a + b

def sub(a, b): 
    return a-b
```

보통 이런식으로 공통적인 기능을 모아둔다.

##### 모듈 사용

현재 같은 디렉토리에 있는 파일을 import 해서 쓸 수 있다.

```python
>>> import mod1
>>> print(mod1.add(3, 4))
7
>>> print(mod1.sub(4, 2))
2
```

모듈 이름 없이, 그냥 함수처럼 쓰고싶은경우에는 __from module_name import method__ 로 사용한다.

```python
>>> from mod1 import add
>>> add(3, 4)
7
```



## pep8

파이썬 공식  코딩 스타일 

<https://www.python.org/dev/peps/pep-0008/>

한국어 가이드

<https://kongdols-room.tistory.com/18>



#### 0이 n 개있는 리스트 만들기

```python
listofzeros = [0] * n
```

