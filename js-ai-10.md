### 상속 & 객체 생성
```typescript
//Book은 EBook의 부모 클래스
let book:Book = new EBook('a', 'b','c');
```

```java
//위와 같은 상황의 코드
class A {...}
class B extends A{...}

A a = new B(); //B a = new B();와 동일한 의미
```
-> B를 생성. 

-> 이렇게 하는 이유.
: A a = new B();를 사용하면 B가 A를 상속한다는 것을 바로 알 수 있음! 

### Modifier(수정자)
- public/protectd/private
```typescript
class Book {

    protected btitle: string;

    public constructor(btitle:string, private _bauthor:string) {
        this.btitle = btitle;
    }

    public printInfo(): void {
        console.log(`제목: ${this.btitle}, 저자: ${this._bauthor}`);
    }

    // private property인 _bauthor의 getter
    get bauthor(): string {
        return this._bauthor;
    }

    // private property인 _bauthor의 setter
    set bauthor(value: string) {
        this._bauthor = value;
    }
}
```
-> protected : 자식클래스에서 부모 클래스의 protected접근 가능
cf) 부모클래스의 private 필드 <-자식 클래스에서 접근 불가 


### 타입스크립트 인터페이스 
```typescript
interface IPerson {
    [idx: string]: string | number | Function;
    myName: string;
    myAddress: string;
    myAge: number;

    printInfo(obj:IPerson): void; // 선언만
}

class Person implements IPerson {
    [index: string]: string | number | Function;
    myName: string;
    myAddress: string;
    myAge: number;

    constructor(name:string, address:string, age:number) {
        this.myName = name;
        this.myAddress = address;
        this.myAge = age;
    }
    
    printInfo(obj: IPerson): void {
        Object.keys(obj).forEach(t => console.log(obj[t]));
    }
}

const obj = new Person("홍길동", "서울", 30);
obj.printInfo(obj);
```

-> 인터페이스 메소드 오버라이드는 오버헤드가 없는 상속
-> 코딩 가이드라인. 

### 도커 실행
- 컨테이너 재시작
$ docker start ubuntu1 
- 컨테이너 접속
$ docker exec -t ubuntu bash  --> #


## Node.js
- Stand-alone javascript(단독실행 가능한 버전의 자바스크립트)
- 서버로 동작가능 
- 자바스크립트에 라이브러리가 추가 
- 크로미움 chromium - blink(HTML파서)/v8(자바스크립트 엔진)
- 자바스크립트 엔진 : webkit(애플) vs v8(구글)

cf)WWW(World-wide Web) = HTML(컨텐츠) + HTTP(전송)
html5= htm+css+ECMAscript+SVG(2D)+Web(3D)

```javascript
//require == import //http모듈(라이브러리) 가져오기
var http = require('http');
//createServer == 서버 생성
http.createServer(function (req, res) { //createServer의 인자로 함수가 들어감
  //http동작 명시
  //브라우저로 접속하면 200(http 응답코드) + Content-Type + html페이지(컨텐트)
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World!');
}).listen(8080);//8080번 포트에 (http)서버를 띄워라
```
cf) 가상머신 포트포워딩
- 버추얼박스 - 설정 - 네트워크 - 고급 - 포트포워딩 - +/- - 8080/8080으로 변경
cf) 도커 포트포워딩 
- docker run -it -p 8080:8080 --name=ubuntu1 ubuntu

-> apt install wget
-> wget http://127.0.0.1:8080


### 네트워크 프로그래밍(서버/클라이언트)
- 네트워크(소켓) 프로그래밍 방식 하나 
- IP(주소) / 포트(0~65535)
: 서버는 포트를 사용 (telnet-23, ftp-21, ssh-22, smtp-25, web-80/8080)
- 서버포트-클라이언트포트 
- OSI 7 계층(TCP/UDP, IP, Ethernet(유선랜)/WIFI(무선랜))

- TCP(connection-oriented 전화와 유사), UDP(connection-less, 문자 방식)

- Request/Response(요청/응답)
- TCP 3-way handshake : SYN -> ACK/SYN -> ACK 

- 브라우저가 요청하는 형식 : GET /a.html HTTP/1.1 
- 서버가 응답하는 형식 : HTTP/1.1 200 OK(상태코드) -> 정상코드(a.html 전송시작) 
cf) 200(정상) / 302(redirection) / 404(file not found)/ 500(server문제)
- **Content-type**
ex) HTML/image(jpg/gif)/avi/mp3...
: 파일의 확장자 대신(네트워크는 확장자x) contentType을 보냄 -> 파일 확장자의 대용
cf)MIME(Multi-purpose Internet Mail Extension) - 메일 스펙 확장 
- MIME type -> Content-type 

		.html -> text/html
		.txt -> text/plain
		.jpg -> image/jpeg
- **Content-length**
: 반드시 헤더와 파일 내용 사이에 빈 줄(\r\n\r\n) 추가

		브라우저의 요청
		GET /a.html HTTP/1.1

		서버의 응답
		HTTP/1.1 200 OK
		CONTENT-TYPE : text/html
		CONTENT-LENGTH: 2000
		(한줄 띄우고)
		<html><head> ...

- HTML인 경우 -> HTML 파서(해석기)(ex-블링크) ->HTML렌더러(페이지 그리기)
