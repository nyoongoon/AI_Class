# 210717 수업


## 자바스크립트의 변수
a = 5; 대입문(assignment)
- var
- let
- const

변수 선언 방식(명시적 선언 vs 묵시적 선언)
		
		                  
var a = 5;(<-요즘 explicit)  VS  a = 5;(<-기존 implicit)

변수 “타입” -> 정수/실수/문자열/불리언

반드시 변수 타입을 선언(string-typed) vs 안해도 알아서 판단(week-typed)
cf) strong-typed -> java/c/c++/c#/…
cf) week-typed -> javascript/python 

1. 변수(var)를 안씀(초창기)
2. var를 선언하세요(ES) //타입은 지정하지 않아도 됨
3. 타입을 지정하세요(strong-typed ->typescript)

1. 반드시 하세요. -> required, mandatory, compulsory
2. 가급적 해주세요. -> recommended
3. 해도되고 안해도 됩니다. ->  optional

- 명명규칙
: 변수이름 가급적 길게 (자바스크립트는 예외!). -> 다운로드 받아야하는 파일(소스)가 길어짐.(커짐) 
- 코딩할 때 길게 짓기 vs 다운드로 받을 때는 짧게
일반저번 자바스크립트 코드 -> minify된 코드버전으로 수정 ->

jQuery.js(standard/development version) vs jQuery.min.js(compressed/production version)

- 변수/함수명
: a1(o) 1a(x)
: a_ / a$ (_와 $만 가능)
: a1 / A1은 다르다. 

## 자바스크립트 오브젝트 -> JSON(javascrip object notation)

let x = {firstName:”john”, lastName:”Doe”}; // Object

[] - bracket / {} - brace / <> - angle bracket

[] -> 자바스크립트 배열
{} -> 자바스크립트 오브젝트

{a:b} -> a(key) b(value)   —> 키를 가지고 값을 참조. cf) sample.a

얼마든지 중첩(nesting) 가능 -> 복잡한 구조 표현 가능. 
배열 안에 오브젝트, 오브젝트 안에 배열, 

## 자바스크립트 이벤트
- <button onclick ~~
->on(click)  : 클릭이라는 이벤트
cf) ontouch, onchange, onmouseoverm, onmouseout, onkeydown, onload … 
### * onload : 브라우저가 페이지 로딩을 완료한 경우 
- -> 1. 조건에 관계없이 실행 보장을 원하면 onload하면 됨 (자바스크립트가 비동기적으로 실행하기 때문)
- -> 2. 성능향상이 됨(async-비동기) —> 싱글 스레드 기반의 비동기처리

- -> html(+javascript)페이지 다운로드를 “모두” 받았다. -> 비동기 특징과 연관
- 자바스크립트는 실행을 하며 페이지를 다운 받기 때문에 보장 또는 확인을 받을 필요가 있음.
- -> callback 함수 (원래의 콜백함수의 뜻이 살짝 다르다) 

- 콜백 함수(조건이 되면 미리 정해진 함수가 실행) 
 : 개발자가 직접 호출하는 함수가 아님.  
cf)자바에서  main() 이 콜백 함수. (약속된 함수) 

## cf) 비동기
- 최근의 가장 이슈 -> Node.js가 비동기를 밀고 있음. 
- + 스프링에서 비동기 기능이 최근에 추가되었음.
- 

## 자바스크립트 함수 

- cf) 프로그래밍에서 예전엔 리턴값이 없는 함수는 subroutine이라고 불렀음. 
- 함수 정의 :
function myFuncion(p1, p2){
return p1 * p2;
}
- 함수 호출(call/invoke)
myFunction(1,2);

- ->자바 스크립트는 함수 정의 후 호출! 

- 함수를 쓰는 이유?
1. 코드 가독성 향상(cf. 리팩터링(인수분해와 유사))
2. 관리 편의성
3. 속도 느려짐 (cf. 함수없애는것->인라인실행)

- 변수 정의  
1. 함수 안에 : 로컬 변수
2. 함수 밖에 : 전역 변수 

로컬변수는 함수호출 시 변수 생성 후, 함수 종료되면 변수 삭제. 
전역변수는 함수 생명주기와 관계없다. 

전역변수 -> 객체지향에서 쓰면 안되는 개념. 

1. 함수 - 인자 넣어 리턴값을 받아서 처리
2 함수에서 전역변수를 참조/전역변수에 결과 출력 -> 다른문제 발생(SW위기) -> 원인(전역변수 사용금지)-> 해결책 객체지향(캡슐화)


