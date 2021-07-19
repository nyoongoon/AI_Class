## 자바스크립트 함수 / 변수

- 함수 기본 개념
- 로컬변수/전역변수
	- 변수 스코프(함수의 유효기간과 같이 감)
- 객체지향에서 전역변수 사용 지양! -> 전역변수의 대체재..? -> 클로저 (closure)
- 변수 vs 함수 
	- 변수 != 함수 vs 변수 == 함수 
  	- 변수를 써야하는 자리에 함수를 넣는 것이 허용. (자바스크립트, 파이썬, 자바8이후)
	- 함수형 언어 
: 자바스크립트에서 함수는 값으로 취급된다. (변수자리 함수 넣을 수 있으)

ex) var a = { b:function(){}};		

## 클로저 (객체지향에서 전역변수의 대체제) - 자스와 자바, 파이썬에 있음. 
``` javasctipt
const add = (function () {
  let counter = 0;
  return function () {counter += 1; return counter}
})();
// ㄴ> self invoking -> 정의하면서 호출.

add();
add();
add();

// the counter is now 3
 ```

## 자바스크립트 let /const
- var하고 스코프가 다름. 
- let == 블록{ } 스코프를 가지는 변수  
- const == 블록 스코프를 가지는 상수

## 익명(1회용) 함수
``` javascript
var sample = function(){..}
```

## 자바스크립트 arrow function (람다 함수) 
``` javascript
(인자) => 리턴값
() =>{return “Hello World!”;}
```

## 자바 비교 연산자
- === 
: equal value and equal type. 
- !==
: not equal value or not equal type.
cf) 
a = 5;
a == 5  -> true
a === “5” ->false

## cf) HTML
- block element : 세로로 나열
- <h1>,<p>
- -> 블럭 엘리멘트를 인라인처럼 출력하려면?  ->CSS에 대해 알아야함
- in-line element : 가로로 나열 
- <span>, <a> —> 줄 바꾸려면 <br/>

## for in (향상된 for문)
``` javascript
const person = {fname:"John", lname:"Doe", age:25};

let text = "";
for (let x in person) {
  text += person[x];
}
```
cf) person.age == person[“age”] -> but 루프에서 쓰려면 []을 써야함! 

## 자바스크립트 Hoisting 

``` javascript
x = 5; // Assign 5 to x

elem = document.getElementById("demo"); // Find an element
elem.innerHTML = x;                     // Display x in the element

var x; // Declare x -> 나중에 선언해도 됨!
```
- 변수를 먼저 사용하고, 나중에 선언해도 실행된다!

## 자바스크립트 use strict
- 제일 첫줄에 “use strict” 
- 스트릭트 모드를 사용하면, 변수 선언후 사용하지 않으면 에러가 뜸.

## 자바스크립트 JSON 
- javasctip object vs JSON —> 같은가 다른가? -> 다름!
- JSON은 그냥 문자열! (형식만 빌려옴) 
- JSON string -> JSON.parse() -> 오브젝트 (자바스크립트)
- 오브젝트 -> JSON.stringify() -> JSON string

``` javascript
let text = '{"employees":[' +
'{"firstName":"John","lastName":"Doe" },' +
'{"firstName":"Anna","lastName":"Smith" },' +
'{"firstName":"Peter","lastName":"Jones" }]}';

const obj = JSON.parse(text);
document.getElementById("demo").innerHTML =
obj.employees[1].firstName + " " + obj.employees[1].lastName;
```
- -> {}은 오브젝트!  //  []은 배열(array)!
- -> employees == key, []JSON == value

### 자바스크립트 HTML DOM
server -> JSON ->download(client) -> HTML converting 
- ->DOM에 대한 이해가 있어야함 cf)Virtual DOM(React)
- DOM( Document Object Model ) 
: HTML 파일 -> parsing(해석) ->DOM 트리로 변환. 

		Document
			|
	Root element: <html>
	/			\
Element			Element
<head>			<body>
	|	           /			\
Element         Element			Element
<title>	        <a>			  <h1>
	|	    /	   	\		      |
Text:		Text:		Attribute:	    Text:
“My title”.   “My link”	“href”	    “My header”

- DOM 네비게이션 : 노드를 부모, 자식, 형제 관계로 만들 수 있음. == 노드를 왔다 갔다 할 수 있음.
- 동적으로 페이지를 수정할 수 있음. 
