## 객체지향 방법론
- OOAD:객체지향분석설계(analysis:분석)&(design:설계) ->UML(그림)-> OOP(programming:코딩) 
- OOAD원칙(객체지향 설계 원칙 (SOLID))
: 객체지향에 대한 평가기준 

### SRP 단일 책임 원칙
: 한 클래스는 하나의 책임(기능)만 가져야한다. 

### OCP 개방 폐쇄 원칙 -> IoC / DI
: 기능 추가에 열려있고 수정에는 닫혀있다
: 전략패턴(starategy pattern) == IoC / DI

- IoC (Inversion of Control)
-> 프레임워크(스프링)/엔진(유니티,언리얼) -> 시키는대로 해라
- DI (Dependency Injection)

## 의존성 (Dependency)
-> 의존한다(사용한다)
-> 나는 핸드폰을 사용한다 == 나는 핸드폰에 의존한다. (나 -> 핸드폰)

: 전체가 **부분에** 의존한다. (전체 -> 부분) 

### cf) UML
- 화살표 머리(실선/점선)
: 화살표 모양의 점선 == 의존성 (전체 -> 부분)
: 화살표 실선 == 방향이 있는 association(연관) cf. 검은/흰 다이아몬드(db관련) 
- 삼각형 머리(실선/점선)
: 삼각형 실선 == 클래스 상속(extends)
: 삼각형 점선 == 인터페이스 상속(implements)

```java
// 의존성 예시
class Sample{
	private String;
	public String getName(){return this.name;}
	public void setName(String name){
		this.name=name;
	}
}
```

- 의존성 : Sample ---> name. (UML표현)
: Sample이 name에 의존한다. (사용한다)

## 주입한다 (Inject)
- 일을 하기 위해서 필요한 의존성
ex) 공간/돈/장비/... 
- 코드 실행에 필요한 모든 것(의존성)들이 있어야 -> 코드 실행이 가능
-> 어떻게 넣지?
1. 생성자를 통한 주입
2. setter를 통한 주입
3. 전용 함수(메소드)를 통한 주입

