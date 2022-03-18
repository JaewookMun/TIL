# 문서 디자인


## 구조
---


### 레이아웃

- z-index : position 속성과 연관이 있기 때문에 position: static 이면 우선순위를 설정할 수 없다. 

<br>

웹화면 구성시 블럭을 가로로 배치하는 방법: float, flex 활용 <br>

_*_ 참고: 블럭 타입 엘리먼트를 inline으로 바꿔서 나열할 경우 뒤에오는 블럭의 내용 배치가 원하는 형태로 오지 않을 수 있다. (경험)

<br>

* float <br>
  
  ``` css
  #대상__블록 {
    float: left;
    float: right;
    float: none;
    width: xy%; /* 너비 속성을 같이 사용 */
    clear: both;  /* 사용 후 초기화 */ 
  }

  ```
left, right, none 세가지 속성값이 있으며 left 또는 right으로 방향을 지정하여 너비를 지정한 후 블럭을 나열한다.
width 값을 주지 않으면 적용된 css를 확인하기 어려움
float이 적용된 영역이 끝나면 'clear: both'를 사용하여 float의 영향이 없도록 처리한다.

<br>

* flex <br>

  ``` css
  #컨테이너 {
    display: block;
  }

  ```

플랙스 컨테이너의 아이템(내부 블럭)들은 가로방향으로 배치되고, 자신이 가진 내용물의 너비만큼 width를 차지하며, height은 컨테이너가 내부의 플랙스 아이템들 중 가장 큰 높이만큼 늘어난다. (eg. A, B, C가 각각 10, 2, 5 px 의 height일 경우 A,B,C를 하위 엘리먼트로 갖는 블럭 Z의 높이는 10px이 됨)





### 테이블

* 반응형 테이블 스크롤 자동생성

``` css
@media (max-width: 575.98px) {}  /* 미디어 쿼리 max width 설정 */

.table-container {
  width: 100%;
  overflow-x: auto;
  white-space: nowrap; /* 해당 속성을 nowrap으로 설정안하면 글자가 세로로 표시. */
}

.table {
  width: auto;
}

```


### 글자 

css 속성값 user-select를 none으로 설정하여 사용자의 글자 드래그를 방지할 수 있다.

``` css
.example {
  user-select: none;  /* 글씨 드래그 방지 */
}


```


<br>




### [참고] <br>
  

  * 레이아웃 [Layout] <br>
  *-* z-index - https://abcdqbbq.tistory.com/39 <br>
  *-* CSS float 사용방법 - https://ojji.wayful.com/2014/01/HTML-DIV-to-Float-Three-Divs-side-by-side.html <br>
  *-* CSS flex 사용방법 [자세함] @@@@ - https://studiomeal.com/archives/197 <br>

  <br>

  *-* 테이블 스크롤(종,횡) 자동생성 방법 - https://dailyscript.tistory.com/entry/%EB%B0%98%EC%9D%91%ED%98%95-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EA%B0%80%EB%A1%9C-%EC%8A%A4%ED%81%AC%EB%A1%A4-%ED%9A%A1%EC%8A%A4%ED%81%AC%EB%A1%A4-%EC%A0%81%EC%9A%A9-%EB%B0%A9%EB%B2%95 <br>
  *-* 글자(폰트) 그림자 - https://mintaku.tistory.com/27 <br>

