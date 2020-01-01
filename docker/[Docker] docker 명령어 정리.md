## Docker 명령어 정리

##### 이미지 검색

```bash
docker search ubuntu
```

##### 이미지 받기

```bash
# :latest 를 설정하면 최신 파일을 받을 수 있다.
docker pull ubuntu:latest
```

##### 이미지 목록 

##### 컨테이너 생성하기

```
docker run -i -t --name hello \ ubuntu /bin/bash
```

##### 컨테이너 목록 확인하기

```
docker ps -a
```

##### 컨테이너 시작하기 

```bash
# hello 라는 이름을 가진 컨테이너를 시작한다.
docker start hello
```

##### 컨테이너 재 시작하기

```
docker restart hello
```

##### 컨테이너에 접속하기

```
docker attach gello
```

##### 컨테이너 정지하기

```
docker stop hello
```

##### 컨테이너 삭제하기

```
docker rm hello
```

##### 이미지 삭제하기

```
docker rmi ubuntu:latest
```

##### 모든 이미지 삭제하기

```
docker rmi $(docker images -q)
```

##### 모든 컨테이너 삭제하기

```
docker rm `docker ps -aq`
```

##### 도커 파일로 이미지를 생성하기

```bash
# 뒤에 점 붙혀야함! 
docker build --tag hello:0.1 .
```

##### 컨테이너 생성하기 

```
docker run --name hello-nginx -d -p 80:80 \ -v /root/data:/data hello:0.1
```

##### 이미지 히스토리 살펴보기

```
docker history hello:0.1
```

##### 컨테이너에서 파일 꺼내기

```
docker cp \ hello-nginx:/etc/nginx/nginx.conf ./
```

##### 컨테이너의 변경 사항을 이미지로 저장하기 

```
docker commit -a "Foo Bar <foo@bar.com>" \ -m "add hello.txt" hello-nginx hello:0.2
```

##### 컨테이너에서 변경된 파일 확인하기

```
docker diff hello-nginx
```

##### 이미지와 컨테이너의 세부 정보 확인하기

```
docker inspect hello-nginx
```



##### 

##### 