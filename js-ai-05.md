### 1급 함수 (fisrt-class citizen)
- 1급 함수 == 1급 시민
- 함수가 다음으로 활용 가능
: 변수자리, 함수의 인자, 함수의 리턴의 리턴값



## XML vs HTML 
- xml : 문서구조 정의(DTD/XMLschema)를 원하는대로
- html : 규정대로 
- xml DOM vs html DOM
: 문서의 내용/형식이 정의대로 되어 있는지 확인 -> 트리를 만들어 확인

- xml DOM vs Simple API for XML (SAX)
: 웹페이지에 <a href="">가 몇 개 인가? -> SAX를 사용하는 것이 편리. 
: BODY아래의 모든 엘리먼트에 대해 속성(CSS)을 변경. -> DOM을 사용해야 함.
- XML SAX에 대응하는 HTML 기능

## DOM Navigation : dom 내의 node들 사이에서 이동(navigate)할 수 있음.
- child"s"[0] -> 첫 번째 자식 
- next sibling / precivous sibling 
- parent 

cf) 모든 DOM 트리의 마지막 노드(leaf)는 반드시 text node! 
ex) <title> has one child (a text node): "text"

- innerHTML은 DOM API가 아님 
: document.getElementById("p").innerHTML
- -> document.getElementById("p").childNodes[0] --> (DOM API로 보았을 경우)

cf) API : 보통 프로그래밍에서 특별한 기능을 가지는 (미리 정해진)함수. (== 유닉스에선 primitive)
ex) print() <- 파이썬 출력 API  

## DOM (Node)생성, 삭제

``` javascript
<div id="div1">
  <p id="p1">This is a paragraph.</p>
  <p id="p2">This is another paragraph.</p>
</div>
///
<script>
const para = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node); /// 마지막에 추가

const element = document.getElementById("div1");
element.appendChild(para);
</script>
```
- cf) insertBefore(para, child); //para를 child 앞에 삽입

