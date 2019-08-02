## HTTP 란

문서를 교환하기 위한 간단한 프로토콜

월드 와이드 웹을 만든 팀 버너스리가 인터넷 시스템을 구현할 때 만든것이

- html
- http
- www 브라우저 
- httpd 초기 버전

이었는데, 이 중 http 는 문서 전송 프로토콜. 

## HTTP/0.9

one line protocol

요청은 단일 라인 구성. get 이 유일한 메서드 

##### example

```
get /mypage.html
```

```html
<html>
    A very simple HTML page
</html>
```

##### 단점

- html 파일만 전송될 수 있고, 다른문서는 전송될 수 없음.

- 상태, 오류코드 x 


## HTTP/1.0

제한적인 문제점을 발전시켰다

- 버전 정보가 요청 사이에 전송
- 상태 코드 전송 - 브라우저가 실패/성공을 알 수 있어, 상태에 따른 여러 동작이 가능해졌다.
- HTTP header 의 도움으로 다른 문서들을 전송하는 기능이 추가되었다. `content-type`

##### example

request

```
GET /mypage.html HTTP/1.0
User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)
```

response

```html
200 OK
Date: Tue, 15 Nov 1994 08:12:31 GMT
Server: CERN/3.0 libwww/2.17
Content-Type: text/html
<HTML> 
A page with an image
  <IMG SRC="/myimage.gif">
</HTML>
```



## HTTP/1.1 - 표준 프로토콜

- 커넥션 재사용. 탐색 된 문서 내에 정보들을 재사용하게 만들어 시간을 절약할 수 있게 하였다.

- 파이 프라이닝 추가. 첫 요청에 대한 응답이 완전 전송되기 전에 두번째 요청 전송을 하능하게 하였다. 

- 청크된 응답 또한 지원

  __청크된 응답__ : 전체 페이지를 가공하지 않고, 서버 측에서 html 일부 생성 후 덩어리 단위로 보낼 수 있게 하는 것. 전체 컨텐츠 크기를 안알려 줘도 된다. 

- 추가적인 캐시 제어 메커니즘

- 언어 / 인코딩 or 타입을 포함한 컨텐츠 도입. 클라이언트 - 서버에 적합한 컨텐츠에 대한 동의를 가능하게 했다

- Host 헤더 등장. 동일 ip 주소에 다른 도메인을 호스팅 하는 기능 생김 



##### example

request

```
GET /en-US/docs/Glossary/Simple_header HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header
```

response

```
200 OK
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Wed, 20 Jul 2016 10:55:30 GMT
Etag: "547fa7e369ef56031dd3bff2ace9fc0832eb251a"
Keep-Alive: timeout=5, max=1000
Last-Modified: Tue, 19 Jul 2016 00:59:33 GMT
Server: Apache
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding
(content)
```



이후 15년 동안 확장 되었다. 



## 보안 전송을 위한 HTTP 사용 

1994년 http 전송할 때 `TCP/IP` 스택을 사용하는 대신, 그 위에 추가적인 암호화 전송 계층인 `SSL` 을 만들어냈다. (현재 TLS 1.3)

##### SSL

웹 서버와 브라우저 사이 보안을 위해 만들었음. ssl 2.0 / ssl 3.0 / ssl 3.1 을 만들어 서버와 클라이언트 간에 교환된 메시지 인증을 암호화 하고 보장. 이로써 e-commerce 웹 사이트가 만들어졌따 

간단히 말해서 데이터를 암호화 해 안전한 통신을 수행하는 시스템. 



## 복잡한 어플리케이션을 위한 HTTP 사용 

2000년 REST API 고안. 서버 전송 이벤트 / 웹 소켓등과 같은 확장이 생김



## 웹의 보안 모델 완화

cors / csp / same-origin 정책 등이 생겼다. 

##### same - origin policy (SOP)

cross - domain 이슈에 대한 근본적인 원인. 다른 포트를 사용할 경우 SOP 에 위반된다.

##### cors (cross-origin resource sharing)

request 에 origin header 를 추가해서 보내면 response 에서 `access-controll-allow-origin` header 를 보내 엑세스를 허용하는 방식. 



## HTTP/2 더 나은 성능을 위한 프로토콜. 

- 텍스트 프로토콜이 아닌 이진 프로토콜 .
- 다중렬 요청이 이루어질 수 있는 다중화 프로토콜. http/1.x 의 프로토콜 에 있ㄴ는 순서를 제거함
- 중복 데이터 오버헤드 제거. 
- 서버로 하여금 사전에 클라이언트 캐시를 넣는다. 