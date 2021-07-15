웹서버 + 웹브라우저

웹브라우저(Chrome-chromium) -> 상당히 큰 프로그램

Cf) chromium(HTTP client ...
    Blink engine(HTMP parser + HTML renderer)
    v8 engine(javascript engine) -> node.js
cf) open source의 약점 -> 라이센스 해결(x) 
    chromium -> 버그픽스+동영상특허 -> chrome

1. 구글이 오픈소스에 적극적 - but -> google.com(검색엔진), Dalvik, AlphaGo - 공개x
2. 애플이 오픈소스에 소극적 - but -> webkit-javascript engine 공개 
    
자바스크립트로 된 HTML 파일을 직접 오픈(x)
서버(아파치/톰캣/nginx) - HTTP로 다운로드(o)

## 자바스크립트 실행환경
- apache/nginx/tomcat8 설치 / 서버 실행 후 URL(http://)로 접근
- node.js 실행 (순수자바스크립트)

## 자바스크립트 교재
w3schools.com
https://ko.javascript.info
http://www.w3big.com/ko/js/default.html


HTML : Hypertext Markup Language
- tag-based language

<h1>, <a>, ...

시작태크 <h1> 마감태그</h1> -> element(엘리먼트, 요소)
<h1>~</h1> -> 전체 내용을 h1(가장 큰 글자)로 표시 

<br/> / <hr/> -> 단독으로만 존재하는 태그
다음줄로 넘겨라 / 가로줄을 그러아

<hr> -> <hr/> ill-formed / well-formed (나쁜 예/좋은 예)
cf)HTML vs XHTML(기업용)
- 자바스크립트의 위치 -> 바디의 마지막에 넣는 것이 좋음
``` html
<html>
	<head>
		<title>Hello World</title>

	</head>
	<body>
		<h1> Hello </h1>
		<script> alert("Hello"); //toast(안드로이드), messagebox
		</sctipt>
	</body>
</html>

// HTML - Javascript 연결 (버튼을 클릭하면 자바스크립트 실행)

<button type="button"
onclick="document.getElementById('demo').innerHTML =  Date()">
Click me to distplay Date and Time.</button>
```
- onclick(이벤트 발생) -> 자바스크립트 코드(주로 함수) 호출

- click -> document.getElementById('demo').innerHTML =  Date()"

<p id = "demo"> innerHTML부분 </p> // paragraph(문단)


## DOM <-- 중요!! (Document Object Model)
- DOM -> Virtual DOM(React)  

document.getElementById('demo') -> demo라는 ID를 가지는 엘리먼트를 찾아달라 <- DOM API 

## 태그(엘리먼트)와 속성(attribute)

- <p id="demo"></p>

- <p></p> -> 태그. 
- id="demo" -> 속성.
ex) <img src=""></img> //속성 == 소스
ex) style -> CSS속성 (색깔, 폰트크기...)




## HTML 이벤트 + 자바스크립트 함수
- HTML 이벤트 -> 자바스크립트 -> 텍스트 내용/속성/스타일 변경(수정)... 

## <!DOCTYPE html>
- HTML5형식의 문서라는 표시 -> parser가 html5문서라고 해석.

cf) W3C -> World-Wide Web Consotium : 웹(XML포함) 표준 제정

## 자바스크립트의 출력 4가지 방법
- innerHTML
- window.alert() 
- document.write() == print() 
- console.log -> 브라우저의 개발자도구 -> 콘솔 탭에 출력 

## 자바스크립트 문법

- 상수(이름부터 잘못) -> 값을 바꿀 수 없는 변수 
- 변수/상수 -> mutable / immutable 
- ES6 이후부터 const
- 자바 : final  int a = 3;
- c++ : const int a = 3;


### whitespace (space/enter/tab) : 칸을 띄우는 것의 총칭.
- 자스는 whitespace 인식
- HTML에서는 빈 칸 여러 개를 한 개로 인식 -> &nbsp; 여러 번 입력


### CamelCase
- Naming convention (명명 규칙)
: 변수 / 함수 / 클래스명 
- 1. 이름을 길게 짓기(직관적으로 이해 가능하도록)
- 2. i_am_a_boy(snake casing) / IAmABoy(pascal casing) / iAmABoy(camel casing)

### JavaScrip character set
- 자바 스크립트는 Unicode 가 표준

cf)ASCII / 완성형(euc-fr/ksc5601) / 유니코드 / utf8(웹에서의 표준)
완성형 ( 영문자/기호 -1바이트, 한글 -2바이트)
유니코드 (한글/영문 2바이트)
utf-8(영어 1바이트, 한글 3바이트)
cf)MS1232(MS949) - MS 윈도우 일부 완성형과 동일/나머지는 다름
완성형 - 28자(x) 11172(o) 
ksc5601-1987(행정전산망)  2350 -> 4888 ... ->11172 
MS(4888까지 따라옴)->codepage -> cp949 (한글)==MS1232
