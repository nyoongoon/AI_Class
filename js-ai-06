## 자바스크립트 비동기
### 콜백 함수 Callback
- 어떤 조건이 충족되면 자동으로 호출되는 함수
ex) 자바 main함수.

- 동기 vs 비동기 
- 동기(Synchronous)
: 함수 호출이 발생하면 함수가 종료되어 리턴될 때까지 대기 == 블럭킹(blocking) 
: 아래 라인이 실행되면 윗라인은 실행이 종료되었다는 의미
: 성능이 떨어짐. 
- 비동기(Asynchronous)
: 함수가 리턴될 때까지 대기하지 않음
: 아래라인이 실행되었다고 해도 윗라인이 실행되지 않을 수도 있다.

- 대부분의 언어는 동기 기반 + 비동기(스레드) 특성 추가 
- 자바스크립트는 기본이 비동기 + 동기식을 보완

- cf)(다른언어)멀티스레드로 실행하면서도 -> 실행순서 보장
 : Synchronization(동기) - semaphore / mutex / critical section... 


 - 자바스크립트 동기화(?)
 - -> callback이 있다.

 ``` javascript
function myDisplayer(some) {
  document.getElementById("demo").innerHTML = some;
}

function myCalculator(num1, num2, myCallback) {
  let sum = num1 + num2;
  myCallback(sum);
}

myCalculator(5, 5, myDisplayer);
 ```
- -> myCalculator(5,5); -> myDisplayer(); (다른언어의 경우)
- -> 자바스크립트를 동기식 실행으로 하기 위해 이렇게 함수의 인자로 함수를 넣어 **콜백함수**로 사용. 


### 정리
: 자바스크립트 기본적으로 비동기 실행
: 동기 실행을 원하면 
1. -> 콜백함수를 사용
2. -> 동기 버전 함수 ex) readFile() vs readFileSync()
 - 하지만 모든 함수의 동기 버전이 있는 것은 아님
3. -> Promise패턴 (ES7)
: 예외처리 코드와 유사하게 구성, 경우의 수를 표현할 수 있게
4. -> Async/Await(ES8)
: 함수 이름 앞에 async -> 비동기 / await 동기
: 사용자가 동기/비동기 실행 선택 가능.

``` javascript
fs.readFile('file.txt', 'utf8', function (err, result) {
    console.log(result);
});
```
- ㄴ> 콜백 함수로 동기식 실행
``` javascript
var result = fs.readFileSync('file.txt', 'utf8');
console.log(result);
```
- ㄴ> 동기 버전 함수로 동기식 힐행
``` javascript
somethingAsync(value1)
    .then((result) => {
        // 성공시 수행할 작업
    })
    .catch((error) => {
        // 실패시 수행할 작업
    });
```
- ㄴ> Promise 패턴으로 동기식 실행
``` javascript
async function myDisplay() {
  let myPromise = new Promise(function(myResolve, myReject) {
    myResolve("I love You !!");
  });
  document.getElementById("demo").innerHTML = await myPromise;
}
```
- ㄴ> async/await


### Time out
- 동기식 실행의 문제점 -> 성능이 떨어짐/ 최악의 경우 응답 없음.
- 해결하기 위해 타임아웃(일정 시간이 넘어가면 강제종료) -> 무한대기방지. 
``` javascript
sync function myDisplay() {
  let myPromise = new Promise(function(myResolve, myReject) {
    setTimeout(function() { myResolve("I love You !!"); }, 3000);
  });
  document.getElementById("demo").innerHTML = await myPromise;
}
```
