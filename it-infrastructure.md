## IT Infrastructure

어플리케이션을 실행하기 위해 필요한 HW, OS, Middleware, Network 등의 시스템 인프라. 시스템 기반에 필요한 사항은 기능적 요구사항과, 비 기능적 요구사항으로 나뉘는데, `IT Infrastructure` 은 비 기능적 요구사항과 관련이 있다. 

__기능적 요구사항__

시스템 기능, 무엇을 하는지

##### 비 기능적 요구사항

시스템 성능, 확장성, 안전성, 보안성 



## 인프라 구성 요소 

### Hardware 

데이터를 저장하기 위한 장치.

##### CPU

코어가 많을 수록 동시 처리 연산이 늘어남. 직렬 처리에 최적화. 

__메모리__

주 기억장치 메모리. 크기가 클수록 좋음

__데이터 스토리지__

데이터를 저장하는 디바이스. 읽기 / 쓰기 속도 영향을 준다. 



### Network

사용자가 원격으로 서버에 접속하기 위한 도구

__네트워크 주소__

장비를 식별하기 위한 주소들이 존재한다

- __MAC 주소__ : 물리적으로 할당되는 48bit 주소
- __IP 주소__ : 인터넷 / 인트라넷 네트워크 장비에 할당되는 번호. 



### OS

하드웨어 / 네트워크 장비를 제어하기 위한 기본적인 소프트웨어. 리소스 / 프로세스 관리 

__OSI 모델__

통신 할 때 어떻게 메세지를 주고 받고 / 어떤 언어를 사용할 지에 대한 규칙. 7 계층으로 나누어져 있다. 

- __물리계층__ : 케이블이 직접 연결되는 계층. 전압 / 전류 값 할당 
- __데이터 링크 계층__ : 동일 네트워크 간 시스템 동신 규정. MAC 정보 추가 / 프레임 단위
- __네트워크 계층__ : 서로 다른 네트워크 간 통신 규정. IP 주소 기반. 패킷 단위
- __전송계층__ : TCP/UDP . 데이터를 전송하는 계층. 메세지를 세그먼트로 나눠 조립
- __세션 계층__ : 앱 간의 연결 유지 / 해제 역할 
- __프레젠테이션 계층__ : 데이터를 앱이 이해할 수 있도록 변환해주는 역할. 데이터 안전 전송 / 암호화 / 복호화
- __응용 계층__ : 최상위 계층. 웹 브라우저 와 같이 사용자가 직접 사용하는 애플리케이션 



### Middle ware

OS 와 애플리케이션 사이에 들어가는 각종 소프트웨어. 웹 서버 / DBMS / 시스템 모니터링 등

__web server__

클라이언트가 보낸 HTTP 요청을 받아 콘텐츠를 반환하거나 서버 쪽 어플리케이션을 호출하는 기능을 가진다. 

