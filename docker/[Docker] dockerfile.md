## dockerfile

도커 컨테이너를 만들 내부 환경을 정리한 페이지. aws ec2 인스턴스 만들 때 사용하는 명령어를 가지고 도커파일을 만들어보았다..(안돌아감ㅠㅠ)

```dockerfile
FROM ubuntu:16:04

MAINTAINER soomtopia@gmail.com

# install packages
RUN apt-get update
RUN apt-get -y install libpq-dev wget curl git build-essential openssl bzip2 patch sqlite

# install node:10
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs

# install ruby 2.6.3
WORKDIR /root
RUN wget -O ruby-install-0.7.0.tar.gz https://github.com/postmodern/ruby-install/archive/v0.7.0.tar.gz
RUN tar -xzvf ruby-install-0.7.0.tar.gz
WORKDIR /root/ruby-install-0.7.0
RUN make install
RUN ruby-install --system ruby 2.6.3
RUN gem update --system
```

##### dockerfile 명령어 알아보기

```dockerfile
# FROM 어떤 이미지를 기반으로 할 지 설정한다. 
FROM ubnutu:16.04

# MAINTAINER : 이미지 작성자 정보를 기록한다 
MAINTAINER soomtopia@gmail.com

# RUN : 이미지에서 스크립트나 명령을 실행한다. 
RUN apt-get update
RUN apt-get -y install libpq-dev wget curl git build-essential openssl bzip2 patch sqlite


# CMD : 컨테이너가 시작 되었을 때 스크립트나 명령을 실행한다. 

# ENTRYPOINT : 컨테이너가 시작되었을때 스크립트나 명령을 실행한다. 

# EXPOSE : 호스트와 연결할 포트 번호를 설정한다

# ENV : 환경 변수 설정

# ADD, COPY : 이미지에 파일을 추가한다

# VOLUME : 데이터를 호스트에게 저장하도록 설정한다

# USER : 명령을 실행할 사용자 계정 설정

# WORKDIR : 명령을 실행할 디렉토리 설정

# ONBUILD : FROM 으로 이미지가 사용될 때 실행할 명령 설정 
```



## 도커 파일 삽질기

혼자 어중 떠중 했는데 망했다..! 

<https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html>

를 보고 다시 시작

```
docker run --rm \
-p 4567:4567 \
-v $PWD:/usr/src/app \
-w /usr/src/app \
ruby \
bash -c "bundle install && bundle exec ruby app.rb -o 0.0.0.0"
```

성공!

------

### 도커파일

도커는 이미지를 만들기위해 단순 텍스트 파일인 이미지 빌드용 DSL(Domain Specific Language) 파일을 사용한다.

고-오급 개발자는 바로 dockerfile 을 만들 고 삽질을 해야한다고 한다. 위안을 받았다..!

##### 도커파일 만들기

**Dockerfile** 이름으로 만들면 된다.

##### 도커파일 실행

```
docker build -t [name] .
```

도커 이미지가 생성된다

```
docker images
```

포트로 실행해보자

```
docker run -d -p 8080:4567 app
```

완성!!! 꺄

도커 태그

```
docker tag sinatra-app soomtopia/sinatra-app:1
docker push soomtopia/sinatra-app:1
```

## 참고자료

- <https://www.redhat.com/ko/topics/virtualization/what-is-virtualization>