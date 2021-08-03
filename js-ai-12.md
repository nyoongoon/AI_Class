## 웹프로그래밍
### GET/POST 명렁어
- 받고(GET) vs 보내고 (POST) 
- 실제로는 보내고 받을 때 다 GET을 사용하게 됨
- GET방식으로 데이터 전송가능 (URL 사용) 
-> "?" : 프로그램명과 인자를 구별
-> "&" : 변수를 구별하는 구별자
-> "=" : 변수와 값을 구별 
cf) URL은 빈 칸이 허용되지 않음. (이스케이프 처리를 해야함)
cf) "%" -> 아스키 코드를 표현하는 특수 기호

- GET/POST 명령어
: GET으로 인자를 넘기는 것이 POST에 비해 간단
: URL의 최대길이 제한 4000자(웹브라우저마다 상이)
- GET으로는 안되는 경우 -> POST
: URL최대 길이가 4000가 넘어가는 경우.
: 인자가 공개되는 것을 원하지 않는 경우

- POST -> 요청바디(REQUEST BODY) 뒤에 첨부 
: 길이 제약은 없다
: 내용이 주소창으로 공개되지 않음 -> 네트워크 덤프(내용출력)하면 내용 알 수 있음.


### REST 방식
- 웹은 아니지만 HTTP를 활용하는 방식
- 웹 기반 CRUD 방식. (DBMS의 CRUD와 유사)
: GET/POST 존재하는 웹과 달리 
: 웹 + 알파 
: 보안 -> 방화벽/공유기 (방화벽 안에 서버가 있는 경우) cf)DMZ(방화벽 밖에 서버)
: 허용된 IP/포트(화이트리스트/블랙리스트) -> http(80/8080),https(443/8443, TSL/SSL) 정도만 허용.
: SCP(원격접속, 파일전송) -> 허용 안 됨.

- HTTP기반의 파일 서비스(crud가능)(모양만 http) -> ex)WebDAV
- --> HTTP 기반 CRUD 인터페이스
: HTTP를 확장(POST/GET/PUT/DELETE) 
ex) WebDAV(파일서버) / 스프링 REST(백엔드 서버) / 엘라스틱 서치(REST) / MSA(GRPC/REST)

- HTTP/REST(텍스트기반) + JSON(메시지포맷)  -> GRPC/REST(바이너리) + JSON

ex) 147.46.114.112(IP주소) -> 4바이트(바이너리로 표현) /14바이트(텍스트로 표현)


### REST vs. RESTful

- GET 명령어는 좀 지저분
- RESTful 예시(pretty URL)
https://search.naver.com/search.naver/create/2405


  
### Node.js - HTTP Module  
- http 모듈
```javascript
var http = require('http');
http.createServer(function(req, res){
        res.writeHead(200, {'Content-Type':'text/html'});
        res.write(req.url);//클라이언트가 요청한 url을 출력
        res.end();
}).listen(8080);
```
- url 모듈
```javascript
var http = require('http');
var url = require('url');
http.createServer(function(req, res){
        res.writeHead(200, {'Content-Type':'text/html'});
        var q=url.parse(req.url, true).query;
        var txt=q.year+" "+q.month
        res.end();
}).listen(8080);
```
-> ex) http://localhost:8080/?year=10&month=October


### Node.js - File System Module 
var fs = require('fs');

```javascript
var http = require('http');
var fs = require('fs');
http.createServer(function (req, res) {
  fs.readFile('demofile1.html', function(err, data) { //demofile.html의 내용을 data로 넣기
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write(data); 
    return res.end();
  });
}).listen(8080);
```

### Node.js - Upload File Module

```javascript
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
  res.write('<input type="file" name="filetoupload"><br>');
  res.write('<input type="submit">');
  res.write('</form>');
  return res.end();
}).listen(8080);
```
- form을 사용.
- action = url을 나타냄. 
- enctyp = 컨텐트 타입
- name = 변수명

```javascript
var http = require('http');
var formidable = require('formidable'); //라이브러리 -> 파일을 조각내 나눠서 보내줌. (sendbuf/recvbuf만큼 나눠서 보냄)

http.createServer(function (req, res) {
  if (req.url == '/fileupload') { //get/post구분하지 않고 받고 있음
    var form = new formidable.IncomingForm();
    form.parse(req, function (err, fields, files) {
      res.write('File uploaded');
      res.end();
    });
  } else { //파일 업로드가 아닌 경우 폼 띄우기  
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write('<form action="fileupload" method="post" enctype="multipart/form-data">');
    res.write('<input type="file" name="filetoupload"><br>');
    res.write('<input type="submit">');
    res.write('</form>');
    return res.end();
  }
}).listen(8080);
```
- 'formidable'설치해야하는 모듈. 
- npm i -S formidable  

### 웹 DBMS 연동 
- DB의 내용을 검색해서 html생성해서 전달
- MySQL(RDBMS) / MongoDB(NoSQL)

### node.js + express.js
- express.js 프레임워크  
- npm install express 
```javascript
const express = require('express');
const app = express();
const port = 8080;

app.get('/', (req, res)=>{
  res.send('Hello World!')
});

app.listen(port ()=>{
  console.log('hello node')
});
```
- 라우팅 기능을 많이 사용 함. 
```javascript
app.route('/boon')
  .get(function(req, res){
    res.send('Get a random book');
  })
  .post(function(req, res){
    res.send('Add a book');
  })
  .put(function(req, res){
    res.send('Update the book');
  });
```






