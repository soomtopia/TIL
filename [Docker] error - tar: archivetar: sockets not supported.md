## tar: archive/tar: sockets not supported

#### problem

앞에는 도커가 저장되어있는 경로가 있고 해당 오류가 나서 검색. 

이 에러가 난 후 데몬이 3G 가 넘게 빌드되길래 이상했다



#### solve

해당 경로를 그냥 폴더 많은 home/ 에 했었는데,  `docker build .`하면 도커는 현재 디렉토리의 내용을  tar up하여 docker 데몬으로 보낸다고 한다. 그 안에 파일이 socket 처럼 보여서 생긴 오류였음.



__특정 디렉토리를 판 후 넣어서 하자!__