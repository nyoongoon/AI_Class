# js-ai-07.md
## 프로그래밍 언어의 흐름
- 절차적(80's)-> 객체지향(90's) -> 함수형(10's-scala/비동기(20's-Typescript)

- 절차적 언어
: C / Javascript 

- 객체지향(Object-oriented)
: 오브젝트 == 사물
: 지향 == 방향 ('=.based) 
: 클래스(붕어빵틀)를 기반으로 오브젝트(붕어빵)를 생성.
:C++/Java/C#/Kotlin/Go/Python/Typescript/Scala
cf) 객체지향은 캡슐화와 상속이 가능해야하는데 js는 캡슐화만 만족. (object는 있지만 상속은 불가)

- 함수형 언어
: 함수의 인자로 함수를 넘김 / 리턴값으로 함수 전달
: 람다함수 
: 코드는 짧지만 난해..
: Scala, Haskel..
: Javascript/Python/Java8

### 절차적 언어의 특징
 - 전역변수 문제(어디서 잘못 됐는지 전체를 봐야함)로 디버깅 시간이 눈덩이처럼 커짐 -> 소프트웨어 위기
 - -> 해결책(객체지향 캡슐화)

### 객체지향의 특징
 - 캡슐화 
 : 클래스의 필드/속성값을 private으로 정의하고 이를 접근하려면 public한 getter/setter(accessor)를 통해 접근하는 형식
 : 정보은닉
 : 어디서 변수를 참조했는지 로그를 남길 수 있음 -> 코로나 qr코드 찍는 것과 비슷 -> 예외가 났을 때, 디버깅 시간을 줄일 수 있음.
- 상속 (cf. 컴포넌트)
: 기존의 코드를 상속받는 형태로 부모클래스의 코드에 기능 추가/ 수정할 수 있는 기능
: "소스레벨"" 코드 재사용 
-> 반쪽짜리라는 비판을 받음(소스코드가 없으면 무용지물)
: 소스코드 재활용 -> "바이너리 레벨"의 코드 재활용-> **컴포넌트** (컴파일 된 후에 재활용-객체지향의 연장 개념)
- ex) MS COM (Component Object Model) : ActiveX / DCOM ... 
- ex) 자바 Beans/Enterprise JavaBean(EJB)/Spring Bean


### 객체지향 기술의 발전
- OOP -> 컴포넌트 -> 서비스 기반 아키텍처(SOA:Service Oriented Architecture) -> 마이크로 서비스 아키텍쳐(MSA:Micro-service Architecture) - 넷플릭스가 잘 함(Netfilx Zuul(OSS) -> Coupang/배민) 

- OOP -> MVC -> DI
- DI -> 스프링 프레임 워크(전자정부프레임워크) / Angular.js 

### POJO(Plain Old Java Object)
- 자바 객체지향의 특징 및 정신을 요약
 - 클래스/인터페이스로 구현할 수 있는 방법을 모두 제공
 - 클래스가 아닌 인터페이스 사용을 선호
 - 특정한 기술/규약에 의존 배격 

### 다중 상속 vs 단일 상속
- 여러개를 상속가능 vs 하나만 상속가능
: 부분상속(x)
: 모든 코드를 다 재활용하지는 않는다. (10개중 메소드 3개 정도만 재활용)
-> 부모클래스는 하나로만 제약(단일상속) - Java/C#/Kotlin/Typescrpt
-> 선택의 문제 
- 당근 -> interface(특수한 클래스) 

### 클래스 / 오브젝트 // 인터페이스
- 클래스/오브젝트 = 코드(메소드/함수) + 데이터(필드/변수)
- 코드의 크기가 훨씬 큼. 
- 인터페이스(클래스의 특수형태) :데이터만 가능/ 코드는 가질 수 없음.
-> 다중 상속 가능. -> 이게 대박 -> **DI**가 **인터페이스** 기반의 패턴
-> 단일상속언어에만 인터페이스가 있음. 
- (코드가 없기 때문에 인터페이스를 다중상속해도 오버헤드가 거의 일어나지 않음)