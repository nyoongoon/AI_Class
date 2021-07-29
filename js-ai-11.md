# 11강 node.js 
``` javascript
var http = require('http'); 

http.createServer(function (req,res){
	res.writeHead(200, {'Content-Type':'text/plain'});
	res.end('Hello World!');
}).listen(8080);
```

		GET http://127.0.0.1:8080 HTTP/1.1 //서버에 파일을 요청(기본파일명index.html)
		HTTP/1.1 200 OK			// 요청한 파일 확인. 이제부터 전송 시작
		CONTENT-TYPE:text/plain	//확장자가 없기 떄문에 콘텐트타입으로 알려줌(.txt형식, content-length 생략)
		// 빈 줄 (HTTP 헤더와 파일의 내용을 분리)
		HelloWorld!	//요청한 파일 내용. -> 타입별로 처리방식이 다름.	

- 타입 별로 다른 처리 방식 
: html인 경우 html 파서(해석기) (크롬:블링크) -> html 렌더러(페이지 그리기)
: image파일 -> JPEG 디코더 -> 비트맵 포맷 
: mp4/mp3 파일 -> 미디어 플레이어 실행 

### HTTP 통신내용 (예시)
- 파일 단위 전송(한 번에 하나의 파일을 다운) -> ex) 네이버 메인에서 파일 받기 -> 166번 요청.
- GET / HTTP/1.1 (index.html - apache/nginx/tomcat, default.htm - IIS(윈도우 서버))
-> 다운로드 -> 연결 종료
-> HTML 파싱 -> <img src="http://127.0.0.1/b.jpg"></img>
-> 이미지를 받기위해 다시 GET / b.jpg HTTP/1.1 (파일을 한번에 하나씩 받는 예시)
<br/>
### 요청받은 파일을 전송 vs 실행 후 결과 전송(ex).jsp/.asp/node.js->javascript 함수 실행) 
- static mode vs dynamic mode(부하가 많이 걸리고 빈도도 많음)
- dynamic mode를 최적화 하기가 주요 이슈가 됨 (static화 ex- 검색 결과 생성 후 저장->캐시) 
<br/>
## HTTP 웹 아키텍쳐
### 클라이언트 단
- 웹브라우저 -> 웹브라우저 캐시 -> 프락시 서버(클라이언트 네트워크 캐시+방화벽)->
### -> 네트워크 장비 (리피터/스위치/라우터/게이트웨이)->
### 리버스 프락시(서버단 캐시(nginx로 많이 함)) -> 로드밸런서(L7/L4스위치)-> 웹 서버 

## HTTP CGI(common gateway interface)
- 웹 다이나믹 컨텐츠 실행 스펙
- 1세대 : 멀티 프로세스 기반(환경변수기반)  -> 일반 프로그래밍 언어
- 2세대 : 멀티쓰레드기반 실행 + 스크립트언어 ex) asp/jsp(=scriptlet/servlet)/php
- 아파치 서버(http 서버 + cgi) + 톰캣(JSP/Servlet)엔진 연동
- HTTP(apache)(80) + 톰캣(8080) 연동
- http://128.0.0.1:80/a.html -> 아파치 응답
- http://128.0.0.1:8080/a.html -> 톰캣 응답
- http://128.0.0.1:80/a.jsp -> 아파치/톰캣 응답

## Node.js는?
-> HTTP 다이나믹 컨텐츠 : 싱글쓰레드 + 비동기기반

### 멀티프로세스 vs 멀티쓰레드 (Thread(실)) vs 싱글쓰레드+비동기
- Batch Processing 
:(a->b->c->d) (싱글 프로세싱이라고 봐도 됨) -> 순서대로, 대기시간 예측불가. 오버헤드는 없음.
- Multi-processing(tasking)
: context-switching(round-robin)(한 순간에 하나의 프로세스-> 정해진 시간(time slice)이 지나면 강제로 정지(preemption) - 실행 중인 내용(context)/ 프로세스간 보호(protection) -> 대략 30%의 오버헤드(context-switching overhead) -> 원하는 시간에 실행 가능. 
- Multi-threading (주류)
: 한 프로세스 안에서의 동시 동작 -> 컨텍스트 스위칭 안해도 됨 (오버헤드 감소) / 보호 없음. 
- **Single Thread + Asynchronous (최신 트렌드) -> Node.js** (Asynchronous Java)
:

cf) 비동기는 성능이 높지만 프로그래밍 하기 어려움 -> 실행은 Asynchronous / 인터페이스(코드)는 Synchronous 를 하고 싶어함

### 동시서버 vs 반복서버
- concurrent: 멀티프로세스(+쓰레드+동기식) vs iterative : 싱글스레드(+비동기)(싱글턴 패턴)

### 싱글턴 패턴
- Singleton : 한개의 인스턴스(오브젝트) 
- 멀티스레트 상황 - 한 개만 제약하기 어려움
- cf) 싱글턴 패턴 in Spring -> 알아서 여러개 만들어(코드에서는 제약없음)
-> 실제로는 내부적으로 하나만 만들어서 제공 -> 성능향상 + 제약없음.

### Content-Length
- 빈 줄 다음부터 실제 파일의 길이 (바이트)
- 텍스트 파일의 경우는 생략 가능 -> 파일의 끝을 알 수 있음
cf) 바이너리 파일 vs 텍스트 파일의 차이
: 텍스트 파일 == 아스키 코드 -> EOF(end-of-file)가 있음. -> eof가 나오면 무조건 종료기 때문에 content-length 없어도 됨
: 바이너리 파일 : 0-255 -> 일반적인 데이터. eof가 없어서 content-length 반드시 필요

