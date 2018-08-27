# HTTP
----

### 만약 브라우저에서 google.com을 입력한다면 내부적으로 어떤일이 발생할 것인가?

- [참조1](https://github.com/alex/what-happens-when)

- [참조2](https://medium.com/@maneesha.wijesinghe1/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a)

- (참조1) 글의 이해가 안되는점..
	- dns 서버에 도달하기 전 arp 절차를 거치는데 arp를 통해 알고자 하는 ip 및 mac address가 무엇인지 정확히 판단이 안됨.. => 목적지 ip,mac인지 dns 서버 ip,mac인지..	

# 1. HTTP 개요

### http

- 신뢰성 있는 전송 프로토콜(tcp / ip)
- jpeg, html, text, wav 등등..

### 웹 클라이언트 서버

- 웹 서버 => http 프로토콜로 의사소통

### 리소스

- 정적파일 : html 워드, pdf, jpeg, avi
- 동적 콘텐츠 : 특정 정보를 가지고 동적인 컨텐츠를 만드는 것.. (웹 컨테이너가 하는일)
- uri
	- url : 한 리소스에 대한 구체적인 위치
	- urn : 리소스의 위치에 영향을 받지 않는 유일무이한 이름(아직 사용하지는 않음...)
	
### 트랜잭션

- request, respose 단위
- 메소드
	- get, put, delete, post, head
- 상태코드
- 웹 페이지는 여러 객체로 이루어 질 수 있다.
	- html, 이미지, javascript 파일, css 파일 기타 등등..
	
### 메시지

- ![이미지](https://mdn.mozillademos.org/files/13827/HTTPMsgStructure2.png)

### tcp 컨넥터

- http는 application 계층이다.
- 신뢰성 있는 연결을 유지하기 위해 tcp를 사용한다.
- ip prot로 서버와 connection을 맺는다.
- http://www.naver.com:80/index.html
- http => 프로토콜, www.naver.com => ip 80, => port, index.html => path

### 프로토콜 버전

- http/1.1, http/2.0

### 웹 구성요소

- proxy
	- 클라이언트와 서버사이에 위치한 중개자
- cache
	- 많은 찾는 웹페이지를 클라이언트 가까이에 보관하는 http 창고
- gateway
	- 다른 application과 연결된 특별한 웹서버
- tunnel
	- 단순히 http 통신을 전달하기만 하는 특별한 proxy(ssl에 사용)
- agent
	- 쟈동화된 http 요청을 만드는 준지능적 클라이언트


	

		


