# Django girls tutorial

> ##### 📓 아래 사이트를 보고 공부한 내용을 작성한 글입니다.
>
> ##### ✅  <https://tutorial.djangogirls.org/ko> 



## 인터넷은 어떻게 동작할까요

#### Website

영상 / 사진 / 글을 묶은 데이터 묶음. HTML 코드가 들어있다.

#### Server

데이터를 저장하고 제공하는 공간

#### Network

여러 서버들이 연결된 망

#### 브라우저에 url 을 입력했을 때 일어나는일

1. 브라우저가 url을 해석합니다.

   일단 URL 을 검사하는데, 문법이 맞는지 확인합니다. 문법이 맞으면 url 에 __퓨니 코드__를 적용합니다. 이후 HSTS 를 확인 후 목록에 있으면 __https__로, 없으면 __https__로 보냅니다. 

   ###### 퓨니코드?

   > 유니코드 문자열을 호스트 이름에서 허용된 문자만으로 인코딩 하는것을 말합니다. 

2. __DNS__ 조회 후 __ARP__ 를 통해 __IP__와 __MAC Address__ 를 알아냅니다.

   ###### IP 

   > 네트워크 통신 기기에 식별된 번호

   ###### MAC ADDRESS

   > 하드웨어 고유 주소 

   ###### ARP (Address Resolution Protocol)

   >  네트워크 상 IP주소를 물리적 네트워크 주소로 대응시키기 위해 사용되는 프로토콜 

3. TCP 통신을 통해 Socket 을 연다

4. HTTP 프로토콜을 요청한다 

5. HTTP 서버가 응답한다



## 장고란 무엇인가요?

python 으로 만들어진 무료 __웹 어플리케이션 프레임워크__

#### 프레임워크

웹사이트 구축 시, 비슷한 유형을 항상 필요로하는데, 공통 요소들을 구성해 갖춘 구조를 말한다. 웹서비스를 만들기 위해 작성하는 구조

>  Django 는 request가 들어오면 urlresolver 가 패턴을 비교함. 일치하는 패턴을 찾아 view(함수)에 전달. 전달받은 view 는 요청 사항을 실행 후 브라우저에 응답



## 장고 설치하기 

#### 가상환경 설치

장고 설치 전, 가상환경 도구를 설치해보자. 가상환경을 사용하면 python / Django 를 분리해준다. 

###### 가상환경을 사용하는 이유?

> 파이썬은 굉장히 많은 라이브러리들이 존재하며, 데이터, 머신러닝 등 다양한 내용들이 사용되는데, 이걸 분리하지 않고 사용하면 버전 충돌이 발생할 경우가 생긴다. 
>
> 보통 pip 로 패키지를 설치하는데, Lib/site-packages 안에 저장되어, __모든 파이썬 스크립트에서__ 사용이 가능하다. 이럴 경우, 여러 프로젝트 개발시에 __패키지 버전문제__가 발생하게 되는 것! 
>
> 예를들어 여러 프로젝트중 같은 패키지에 다른 버전을 사용하고, 호환이 불가능하면 상당히 불편해진다.
>
> 가상환경을 사용하면 패키지가 가상 환경 안에 생기고, 인터프리터 또한 가상환경에 설치된다. 

##### venv 설치

```shell
$ python3 -m venv (name) 
```

##### venv 실행

```shell
$ source myvenv/bin/activate

#(myvenv) $ls
#myvenv
#(myvenv) $cd myvenv/
#(myvenv) /myvenv$ls
#bin		include		lib		pyvenv.cfg
```



## Django 설치하기

가상환경 안에 django 를 설치해보자

##### 1. pip 최신버전 업그레이드

```
python3 -m pip install --upgrade pip
```

###### pip

python 패키지 라이브러리. ruby 의 gem 같이 파이썬 라이브러리를 관리해주는 시스템

##### 2. django 설치

```
pip install django~=2.0.0
```

pip 를 통해 장고를 설치해준다

## 참고자료

- <https://tutorial.djangogirls.org/ko/django_installation/>

- <https://dojang.io/mod/page/view.php?id=2470>



## 나의 첫 번째 장고 프로젝트!

장고 프로젝트 설치

```python
$ django-admin startproject mysite . #현재 폴더에 mysite 프로젝트를 생성해라! 
```

> 해당 명령어 진행시, db설정, django 옵션, app 설정 인스턴스와 같은 인스턴스 구성 설정들이 생성된다.

##### 폴더 구조

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

###### mysite/ 

프로젝트 최상위 폴더. 이름은 마음대로 변경 가능하다. 

###### manage.py

django 프로젝트와 여러 상호작용을 하는 파일. 해당 파일을 통해 컴퓨터에 어떤 설치작업 없이 웹 서버 시작이 가능하다.

```python
#!/usr/bin/env python
import os
import sys

if __name__ == "__main__":
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "mysite.settings")
    try:
        from django.core.management import execute_from_command_line
    except ImportError as exc:
        raise ImportError(
            "Couldn't import Django. Are you sure it's installed and "
            "available on your PYTHONPATH environment variable? Did you "
            "forget to activate a virtual environment?"
        ) from exc
    execute_from_command_line(sys.argv)
~    


# DJANGO_SETTINGS_MODULE
# 파이썬 문법 경로를 잡아주는 모듈. mysite.settings 에서 보통 python path 를 import 해주는듯
```

###### 내부 mysite/

프로젝트를 위한 파이썬 패키지들이 저장되는 공간. 이 이름을 통해 프로젝트 어디서든, python package import 가 가능하다 

###### manage.py

장고 프로젝트와 상호작용하는 스크립트. 사이트 관리를 도와준다.

###### mysite/__init__.py

python에게 이 디렉토리를 패키지처럼 다루라고 알려주는 용도. 빈 파일이다. 

###### mysite/settings.py

Django 프로젝트 파일 설정. 기본적으로 설정해야되는 시간, 경로 같은 내용들을 여기에 설정해준다.

###### mysite/urls.py

Django 프로젝트의 url 선언 저장. url resolver 를 말하는듯 ??

###### wsgi.py

현재 프로젝트를 서비스하기 위한 웹 서버의 진입점



##### TIMEZONE 변경하기

settings.py

```python
 TIME_ZONE = 'Asia/Seoul'
```

##### 정적 파일 경로 추가

settings.py

```python
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

##### 데이터베이스 설정

settings.py

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

##### django 실행하기

```python
$ python manage.py migrate # models 의 변경사항을 적용해준다. db 변경해서 사용한듯?
```

```python
$ python manage.py runserver
```



## 장고 모델

##### 목적

> 모든 게시글을 저장하는 부분들을 만들자. 

#### 객체

객체 지향 프로그래밍. 모델을 만들어, 그 모델이 어떤 역할을 가지고 어떻게 행동해야 하는지 정의하여 상호작용 할 수 있는 것.

##### 고양이 모델링

```
- 색
- 나이
- 분위기
- 주인

- voice()
- scatch()
- eat(food)
```

객체지향은 속성 / 기능 으로 분류가 된다. 



게시판 객체를 만들어보자

##### posts modeling

```
- 작성시간
- 작성자
- 제목
- 내용

- 수정(k)
- 삭제(k)
- 등록()
- 읽기(k)
```



#### 장고 모델 만들기 

장고 프로젝트 내부에 별도의 어플리케이션을 만들어보자

```python
python manage.py startapp blog
```

이러면 해당 blog 디렉토리가 생성된다.

```python
blog
- migrations/
	- init.py
- init.py
- admin.py
- models.py
- views.py
- tests.py
```

app을 생성하면 `settings.py` 에 config 설정을 해주어야 한다. 

`INSTALLED_APPS` 파일에 블로그를 추가하자. 



#### 블로그 글 모델 만들기

`blog/models.py` 파일에 모델을 선언한다. 

```python
from django.conf import settings
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    
```

##### class Post(models.model)

> 모델을 정의하는 코드. (models.model)을 통해 django model database 를 사용한다

##### attr = models.Field(optional)

> 모델 속성을 정의하는 코드. 
>
> - 변수이름은 모델 속성 이름이다. 
> - django.models 타입에 있는 데이터 종류를 통해 데이터타입을 지정한다. 
>   - CharField - 글자수가 제한된 텍스트 정의
>   - TextField - 글자 수 제한이 없는 텍스트 속성
>   - DateTimeField - 날짜와 시간 의미
>   - ForeignKey - 다른 모델에 대한 링크 

#### 

#### 데이터베이스에 모델을 위한 테이블 만들기

장고 모델을 작성한걸 django project 에 명령을 알려주어야 한다. 바로 반영이 할 수 있도록 migration file 에 실제 모델 추가 명령어를 작성하면 된다. 

```python
$ python manage.py makemigrations blog
```



## 장고 관리자

장고 관리자 화면 blog/admin.py 변경하기

```python 
# django 에서 지원해주는 contrib lbi 중 admin 사용
# Post 모델 사용 
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

##### 서버 실행하기 

```python
$ python manage.py runserver
```

<http://127.0.0.1:8000/admin/login/?next=/admin/> 사이트로 들어가면, admin 관리 사이트가 나오는데, 로그인하라고 뜬다. 슈퍼 유저를 행성해보자

##### 슈퍼 유저 생성

```python
$ python manage.py createsuperuser

# Username (leave blank to use 'soomti'): soomin
# Email address: soom93@gmail.com
# Password: 
# Password (again): 
```



## Django urls

##### url 이란?

웹 주소. 모든 웹 페이지는 url 을 가지고 있어야 한다. 장고는 `URLconf (URL configuration)` 를 사용한다. URL 과 일치하는 뷰를 찾기 위한 패턴들의 집합이다. 

##### docstring - """ or '''

파일 제일 첫 부분, 클래스 또는 메서드 윗 부분에 작성해, 이들이 어떤 일을 수행하는지 알려준다. 파이썬은 이 부분을 실행하지 않을 거에요.

###### function-view classed-view 차이

> urls.py docstring 에 
>
> ```
> """mysite URL Configuration
> 
> The `urlpatterns` list routes URLs to views. For more information please see:
>     https://docs.djangoproject.com/en/2.0/topics/http/urls/
> Examples:
> Function views
>     1. Add an import:  from my_app import views
>     2. Add a URL to urlpatterns:  path('', views.home, name='home')
> Class-based views
>     1. Add an import:  from other_app.views import Home
>     2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
> Including another URLconf
>     1. Import the include() function: from django.urls import include, path
>     2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
> """
> ```
>
> 요 부분이 궁금해서 찾음. < 나중에 필기해보기 







