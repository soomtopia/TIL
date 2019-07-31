## Docker

**컨테이너 기반 오픈소스 가상화 플랫폼.**

기본적으로 개발할 때 모든 사람들이 환경이 같지 않다. (window/mac/linux). 각 운영체제마다 설정 환경이 달라서 맞추는것도 고역인데, 도커를 사용하면 어느 환경이던 도커 사용해서 바로 띄울 수 있기 때문에 배포할 때 편하다는 장점이 있다.

기존 가상환경에서 Mac OSX 위에 다른 os 가올라가는 형식인데, 도커는 반 가상화를 통해 전체 OSX 를 가상화 하지 않아 편리하다. 



##### 컨테이너

다양한 프로그램 / 실행환경을 컨테이너에 묶어 동일한 인터페이스 제공하여 프로그램의 배포 / 관리를 쉽게 해줄 수 있다. 



##### 도커 이미지

도커 이미지란 컨테이너를 생성하기 위해 필요한 설계도. 컨테이너를 생성하기 위한 파일. 해당 파일은 docker hub 에 저장됨. 이미지는 클래스, 컨테이너는 객체 개념인 것 같다. 



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

