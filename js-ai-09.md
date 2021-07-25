# Typescipt

### 인터페이스 -> DI
- 인터페이스 == 코드 재활용이 없는 상속
: 기존 다중상속에서 재활용되지 않는 코드가 많음.
: 코딩 가이드라인(메소드)제시(제약을 통한) 
-> 상속시 반드시 구현되어 있어야 함

- 인터페이스를 구현한 클래스 (UML 삼각형 점선)

- DI 예시
cf) RFP (Request For Proposal)
: 운영체제 리눅스 / 데이터베이스는 오라클 일수도 MySQL일수도 (둘 다 안되나?)
(--> 오라클을 다루는 클래스와 MySQL 다루는 클래스가 같은 인터페이스를 구현하게 작성!)
-> 서비스 ---> 데이터베이스에 의존(DI로 해결 가능)

### Typescript는 Transpiler 언어 
- Typescript는 객체지향언어 -> 컴파일 -> 자바스크립트 코드 생성 -> 인터프리터
- 이렇게 하면 호환성이 높아짐 / 컴파일+인터프리팅
- MS가 만들고 -> Angular에서 필수(구글) 

## Typescript(+Node.js) 환경 구축 && 실행
- Node.js -> npm(패키지 매니저) -> typescript 설치 

		-> apt install nodejs
		-> apt install npm
		-> npm install -g typscript
		-> apt install nano
		-> nano sample.ts (타입스크립트 확장자)
		-> tsc ---init -> tsconfig.json 생성
		-> tsc sample.ts (컴파일 - ES버전 지정 가능)
		-> ls -> sample.js (js파일로 변환되어 있음)
		-> node sample.js || nodejs sample.js (실행)

- 도커설치
- 우분투 컨테이너 실행 
- 명령프롬프트에서 
- $ docker run -it --name=ubuntu1 ubuntu
- -> #

### 타입 스크립트 문법
https://moon9342.github.io/typescript-class

``` typescript
class Greeting {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    sayHello() {
        return "Hello " + this.greeting;
    }
}

let tmp = new Greeting("World!!");

console.log(tmp.sayHello());
```
- 컴파일 하면
```javascript
var Greeting = /** @class */ (function () {
    function Greeting(message) {
        this.greeting = message;
    }
    Greeting.prototype.sayHello = function () {
        return "Hello " + this.greeting;
    };
    return Greeting;
}());
var tmp = new Greeting("World!!");
console.log(tmp.sayHello());
```
- 로 변환 되었음
- -> node 명령어로 js파일 실행 

### cf) 객체지향 프로그래밍의 4단계 
1. 클래스 정의 - 필드 / 메소드 정의
``` java
class A {...}
```
2. 객체(오브젝트) 선언 
``` java
A a;
```
3. 객체(오브젝트) 생성
```java
a = new A(); //A a = new A(); 선언과 생성을 동시에  
```
4. 메소드 호출 
```java
a.setGreeting(5);
```

### 타입스크립트 변수 선언
```typescript
let sample : string; //자바 String sample = "";
```
- UML 방식과 흡사함 -> **변수 이름 : 데이터 타입**

### 타입스크립트 클래스 상속
- 오버라이드(override)
: 갈아엎기 
: 부모클래스의 동일한 이름의 메소드를 새로 재정의
- 자식이 만든 printinfo()가 기본적으로 호출 
: this.printinfo vs super.printinfo() <br/>
--> cf) super 메소드를 호출해도 부모의 메소드를 호출한 것이 아니고 **부모에게 상속받은 자식의 메소드를 호출**하는 것! 
