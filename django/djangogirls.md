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