## Http 써보기

http 1.1 과 2.0 차이를 공부했는데. 확실히 이해한건, 

- 2.0 에서는 개발자가 우선순위를 지정할 수 있고.

- 1.1 에서는 텍스트 형식으로 데이터를 받기 때문에 오버헤드가 증가하는데, 2.0 에서는 바이너리 형식으로 전달 / 압축 되기 때문에 해당 문제점을 해결했다는 사실. 

내가 했던 서비스는 1.1 인데, 어떻게 바뀌는지 궁금해서 찾아봤다. 



## rails project 생성

```
$ rails new project
```

해당 프로젝트를 local 에서 돌렸을 때 http 버전은 1.1 이였다.

```
curl -I localho~$curl -I localhost:3000
HTTP/1.1 200 OK
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: text/html; charset=utf-8
ETag: W/"f49408c18e5cbc0b48f4dc9ec0f596d9"
Cache-Control: max-age=0, private, must-revalidate
Content-Security-Policy: script-src 'unsafe-inline'; style-src 'unsafe-inline'
X-Request-Id: b2de8cd8-dea6-414e-be49-5b608ccb84f6
X-Runtime: 0.147938
```

이걸 한번 2.0 으로 바꿔보겠다.  