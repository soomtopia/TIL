## pip

<https://pypi.org/> 에있는 라이브러리를 설치할 수 있는 패키지 관리 시스템

어떤 라이브러리가 필요한 경우, 다운받은후 프로젝트에 적용해야되는데, 여러 라이브러리를 쓰는경우 한번에 관리하기가 힘들다. 따라서 라이브러리를 편리하게 사용하기 위해 __pip__ 를 쓴다. 



##### 버전 확인

```python
$ pip --version
#pip 19.3.1 from /Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/site-packages/pip (python 3.7)
```

보통 python3 을 사용하기때문에 pip, python3 을 alias 를 통해 맞춰 놓았당 

```python
$ alias python=python3
$ python
# Python 3.7.2 (v3.7.2:9a3ffc0492, Dec 24 2018, 02:44:43) 
```

별명 해제하기

```python
$ unalias python
```



##### 주요 명령어

help

```python
$ pip help
```

설치

```python
$ pip install <name>
```

pip 버전 업데이트

```python
$ pip install --upgrade
```

검색

```python
$ pip search <name>
```

삭제

```python
$ pip uninstall <name>
```

pip 목록 출력하기

```python
$ pip freeze
```

> `pip list` 도 목록을 출력하지만, 형식이 다르다. 

mac osx 나 linux 는 __`>`__ 명령어를 통해 출력된 내용을 파일형식으로 저장할 수 있다.

```python
$ pip freeze > requirements.txt
```

freeze 를 통해 다른가상환경에 바로 파일 만들어서 사용하기 좋다.



##### requirements.txt

파이썬 패키지 목록을 저장해두는 파일 이름을 대개 requirements 로 작성한다. (파이썬 문화) 한 파일에 목록을 작성 후 

```python
$ pip install -r requirements.txt
```

의 명령어를 통해 설치한다면, 파일 안에 있는 패키지 리스트들을 모두 설치해준다. `-r` 뒤에는 파일 경로를 작성해주면 된다.



##### 구동환경 별 파이썬 패키지가 다른 경우

맥 / 윈도우일경우, aws 라이브러리일 경우 별도로 requirements.txt  파일을 만든다.

보통, __reqs__ 라는 폴더를 만든 후 이 안에 공통용 / 로컬용 / 개발용 같은 requirements 파일을 다양하게 만든다. 

라이브러리 버전은 명확히! 

