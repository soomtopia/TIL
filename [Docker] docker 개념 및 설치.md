## Docker

###### 세줄요약

```
- 컨테이너 기반 오픈소스 가상화 플랫폼
- 컴퓨터 성능을 효율적으로 사용할 수 있다
- 배포 관리에 편하다
```

![docker logo](https://live.staticflickr.com/7336/14098888813_1047e39f08.jpg)



기본적으로, 회사에 들어가거나 프로젝트를 진행하다보면 모든 사람들이 같은 환경을 가지고 있지 않다. 누구는 그램 / 누구는 맥 등등 ! 각 컴퓨터에 동일한 버전으로 설치를 했다고 할지라도, 뭔가 요상하게 깨지는 일들도 경험해 본적이 있을 것이다. 이런 고역을 피하기 위해 __Docker__ 를 활용해서 개발 환경을 맞추고 배포 관리도 편하게 할 수 있다! 



## 가상화

가상화를 통해 하드웨어의 물리적 리소스를 최대한 활용할 수 있다. 



![visualization](https://www.redhat.com/cms/managed-files/server-usage-500x131.png)

기존에는 1개의 서버에 30%의 서버를 사용하더라도 여러개의 서버를 하나의 서버에 처리하기 어려워, 비효율적이라는 단점이 있었다. 하지만 가상화를 통해서 1개의 서버를 2개의 고유한 서버로 분할 해 각각의 독립적인 태스크를 처리하여, 효율적으로 서버를 사용할 수 있다.

![virtualization](https://www.redhat.com/cms/managed-files/server-usage-for-virtualization-500x131.png)

이렇게 하면 빈 서버를 사용해 다른 태스크를 처리하거나 / 비용을 절감할 수 있다.

가상화에는 호스트형 가상화 / 하이퍼바이저 형 가상화 / 컨테이너 가상화가 있다. 

__호스트형 가상화__

호스트 형 가상화는 하드웨어 위에 `HOST OS` 를 설치하고 가상화 소프트웨어를 이용해 OS 를 작동하는 방식. 가상 환경을 쉽게 구축할 수 있지만,OS 상에서 또다른 OS 가 돌아가므로 자원이 많이 소비되고 느리다. 

##### __하이퍼바이저형 가상화__

__VM__ 의 경우 `hypervisor` 라는 소프트웨어를 통해 물리 리소스를 분리하는 것. 해당 소프트웨어가 하드웨어와 가상 환경을 제어하는데, `host os` 를 사용하지 않지만, 각각의  VM 에서 guest os 가 돌아가기 때문에 가상환경이 시작할 때 걸리는 오버 헤드가 커진다. 

__container 가상화__ 

__VM__ 의 단점인 오버헤드를 최소화 하기 위한 방법으로, HOST OS 상에 독립적인 공간을 만들어, 별도의 서버인 것 처럼 사용한다. 각 어플리케이션이 HOST OS 를 공유하기 때문에 오버헤드가 작아진다. 



![vm vs docker](https://miro.medium.com/max/1400/1*wOBkzBpi1Hl9Nr__Jszplg.png)

VM 의 경우 hypervisor 위에 여러 guest os 가 올라가기 때문에 볼륨이 도커보다 크다. 하지만 도커는 host os 를 공유하기 때문에 해당 볼륨이 작을 뿐더러, docker 의 라이프 사이클은 docker hub 에서 image 를 pull 받으면서 시작하기 때문에, 용량이 훨신 작아 네트워크를 덜 쓰기 때문에 비용도 줄어든다. 



##### 컨테이너

다양한 프로그램 / 실행환경을 컨테이너에 묶어 동일한 인터페이스 제공하여 
프로그램의 배포 / 관리를 쉽게 해줄 수 있는 도구



##### 도커 이미지

도커 이미지란 컨테이너를 생성하기 위해 필요한 설계도. 컨테이너를 생성하기 위한 파일. 
해당 파일은 docker hub 에 저장됨. 이미지는 클래스, 컨테이너는 객체 개념인 것 같다. 



## Getting started

도커 설치 (mac osx)

<https://docs.docker.com/docker-for-mac/install/>

##### terminal 

도커가 잘 설치되어있는지 테스트 해보기 

```bash
$ docker --version
# Docker version 18.09.2, build 6247962
```

##### 도커 이미지 만들기 

```bash
$ docker run hello-world
#Unable to find image 'hello-world:latest' locally
#latest: Pulling from library/hello-world
#1b930d010525: Pull complete 
#Digest: sha256:6540fc08ee6e6b7b63468dc3317e3303aae178cb8a45ed3123180328bcc1d20f
#Status: Downloaded newer image for hello-world:latest

#Hello from Docker!
#This message shows that your installation appears to be working correctly.

```

##### 이미지 다운로드 

```bash
$ docker pull ubuntu
$ cat /etc/issue # 우분투 버전 확인
```

내 레포에 없으면 공식적인 문서를 가져온다. run 을 했을 경우 없으면 pull 후 실행.

##### 도커 실행 컨테이너 확인

```bash
$ docker ps
```

##### 도커 이미지 리스트

```bash
$ docker image ls
```

##### 도커 컨테이너 생성

```bash
$ docker run -i -t --name ubuntu-ruby ubuntu:16.04 /bin/bash
```

##### 도커 컨테이너 종료

```bash
$ docker kill [이름] /bin/bash 
```

##### 도커 이미지 / 컨테이너 강제 삭제

```bash
$ docker rmi -f
```

##### 컨테이너 재부팅 

```bash
$ docker restart [container_id]
```

##### 컨테이너 접속하기

```bash
$ docker start [name]
$ docker attach [container_id]
```



##### 컨테이너 삭제

```bash
# 현재 실행중인 모든 컨테이너 강제 종료
$ docker kill $(docker ps -q -f status=running)   
# 현재 실행중인 모든 컨테이너 종료
$ docker stop $(docker ps -q -f status=running)   
# 종료된 모든 컨테이너 삭제
$ docker rm $(docker ps -q -f status=exited)      
```



## 도커 파일 만들기

도커 파일은 이미지를 생성하기 위한 스크립트. rails - ubuntu 환경을 한번에 만들기 위해 사용하기 좋다 

```bash
$ touch Dockerfile
# FROM ubuntu:14.04
```

이름을 도커 파일로 만들면 된다. 

```bash
$ docker build -t fromtest:0.0 
# -t : 새롭게 생성될 이미지 이름 
```

##### add

build 명령어 중 호스트의 파일 시스템으로 부터 파일을 가져오는 것. 

```bash
$ echo "hello" >> test.txt
$ touch dockerfile
# ADD test.txt
```

이런식으로 파일을 넣으면 안에 스크립트가 실행된다. 



## 도커파일로 이미지 만들기 연습 

내가만든 도커파일

rails-nginx-sqlite

```dockerfile
FROM ubnutu:16.04

# install basic packages 
RUN sudo apt-get update
RUN sudo apt-get install -qq -y git curl sqlite3 build-essential openssl wget zlib1g-dev libssl-dev

# install Node.js

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get -qq -y install -y nodejs

# install ruby 

RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(rbenv init -)"' >> ~/.bashrc
RUN exec $SHELL
RUN git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN rbenv install 2.4.3
RUN rbenv global 2.4.3 
RUN echo "gem: --no-document" > ~/.gemrc
RUN gem install bundler
RUN rbenv rehash

# install rails

RUN gem install rails -v 5.2.0 --no-ri --no-rdoc
RUN rbenv rehash
RUN rails -vn

# install nginx 

RUN sudo apt-get -qq -y install dirmngr gnupg
RUN sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 561F9B9CAC40B2F7
RUN sudo apt-get install -y apt-transport-https ca-certificates
RUN sudo sh -c 'echo deb https://oss-binaries.phusionpassenger.com/apt/passenger xenial main > /etc/apt/sources.list.d/passenger.list'
RUN sudo apt-get update
RUN sudo apt-get install -y nginx-extras passenger
```

!!!

뭔가 망했다.. !!!무서워서 끄고 

<https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html>

를 보고 다시 시작 

##### 도커파일

도커는 이미지를 만들기위해 단순 텍스트 파일인 이미지 빌드용 DSL(Domain Specific Language) 파일을 사용한다.

고-오급 개발자는 바로 dockerfile 을 만들 고 삽질을 해야한다고 한다. 위안을 받았다..!

## 참고자료

- <https://www.redhat.com/ko/topics/virtualization/what-is-virtualization>

