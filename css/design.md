# 문서 디자인


<br>

## 구조 (레이아웃)
---

### 미디어 쿼리

단말기의 유형과 특성이나 수치(화면 해상도, 뷰포트 너비 등)에 따라 웹사이트나 앱을 수정할 때 사용하기 용이함

_*_ 뷰포트(viewport)는 현재 화면에 보여지고 있는 다각형(보통 직사각형)의 영역입니다. <br>
 웹 브라우저에서는 현재 창에서 문서를 볼 수 있는 부분(전체화면이라면 화면 전체)을 말합니다
-> 반응형 웹사이트를 만들기 위해서 html 문서의 head에 viewport와 관련된 meta 태그를 넣어줘야함.

<br>

min-width or max-width 를 활용하여 페이지 사이즈에 반응하는 웹페이지를 구성가능


사용 예시
``` css
@media (min-width: 1000px) {
	body {
		background: gold;
	}
}

```


<br><br><br>




### 블럭 배치

<br>

* z-index : position 속성과 연관이 있기 때문에 position: static 이면 우선순위를 설정할 수 없다. 

<br>

웹화면 구성시 블럭을 가로로 배치하는 방법: float, flex 활용 <br>

_*_ 참고: 블럭 타입 엘리먼트를 inline으로 바꿔서 나열할 경우 뒤에오는 블럭의 내용 배치가 원하는 형태로 오지 않을 수 있다. (경험)

<br>

* float : 엘리먼트를 나열하여 배치하는데 사용 가능 (flex 사용 권장)<br>
  
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
float이 적용된 영역이 끝나면 'clear: both'를 사용하여 float의 영향이 없도록 처리하며 아래의 처리 방법 사용을 권장한다.

``` css
/* 가상요소를 사용 */
float된 요소의 부모태그::after {

   content:'';

   display:block;

   clear:both;

}

```

_*_ : - 가상선택자 / :: - 가상요소
> div:hover  | div::after

<br>

* flex <br>

  ``` css
  #컨테이너 {
    display: block;
  }

  ```

플랙스 컨테이너의 아이템(내부 블럭)들은 가로방향으로 배치되고, 자신이 가진 내용물의 너비만큼 width를 차지하며, height은 컨테이너가 내부의 플랙스 아이템들 중 가장 큰 높이만큼 늘어난다. (eg. A, B, C가 각각 10, 2, 5 px 의 height일 경우 A,B,C를 하위 엘리먼트로 갖는 블럭 Z의 높이는 10px이 됨)

<br><br><br>





### 글자 관리 - 영역내 컨텐츠

* white-space : (**공백 처리**) 공백 문자를 처리하는 방법을 지정 (스페이스바, 탭)
  > value : normal(default), nowrap, pre, pre-wrap, pre-line

* word-break : (**줄바뀜 처리**) 텍스트가 자신의 콘텐츠 박스 밖으로 오버플로 할 때 줄을 바꿀지 지정

* text-overflow : 긴 문자열을 잘라주는 방법 지정

* overflow : 값에 따라 스크롤바 생성가능


<br>



<br><br><br>






### 테이블

* table-layout : 테이블의 행, 열, 셀을 배치하는 알고리즘을 설정하는 속성
  > value : auto(default), fixed

  - auto : By default, most browsers use an automatic table layout algorithm. The widths of the table and its cells are adjusted to fit the content.
  - fixed : Table and column widths are set by the widths of table and col elements or by the width of the first row of cells. Cells in subsequent rows do not affect column widths.

  _*_ auto는 셀의 content 길이에 따라 테이블의 width가 변할 수 있지만 fixed는 table header(또는 table)의 width에 고정된다. 



<br><br><br>



<br><br><br>


* 반응형 테이블 스크롤 자동생성

``` css

/* 방식 1 css */
.table-container {
  width: 100%;
  overflow-x: auto;
  white-space: nowrap; /* 해당 속성을 nowrap으로 설정안하면 글자가 세로로 표시(웹 width가 변경됨에 따라 word-breaking이 발생하여 세로로 표시된다.). nowrap은 <br>만 줄바뀜처리로 인식 */
}

.table {
  width: auto;
}


/* 방식 2 css  좀더 깔끔 - 해당방식 적용 */

#container {
	width: 100%;
	overflow: auto;
}

#container table {
	width: 100%;
	table-layout: fixed;
	margin-bottom: 5px;
}

#container table .no {width: 50px;}
#container table .name {width: 120px;}
#container table .id {width: 150px;}
#container table .add1 {width: 200px;}
#container table .add2 {width: 200px;}
#container table .zip {width: 70px;}

```

``` html
<!-- HTML -->
~
<div id="container">
  <table>
    <thead>
      <tr>
        <th class="no">no</th>
        <th class="name">name</th>
        <th class="id">loginId</th>
        <th class="add1">address1</th>
        <th class="add2">address2</th>
        <th class="zip">zip code</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td>john</td>
        <td>john12</td>
        <td>James Street 23-1, Arizona</td>
        <td>the USA</td>
        <td>403-12</td>
      </tr>
    </tbody>
  </table>
</div>

~

```


<br><br><br>


* .table-responsive 스크롤바 보이게 하는법 <br>
  (.table-responsive를 통해서는 투명 스크롤바가 생성된다.)

<br>

``` css
  .table-responsive::-webkit-scrollbar {
      -webkit-appearance: none;
  }

  /* ~:vertical, ~:horizontal의 경우 css를 적용하지 않아도 상관 없어보임. */
  .table-responsive::-webkit-scrollbar:vertical {
      width: 12px;
  }

  .table-responsive::-webkit-scrollbar:horizontal {
      height: 12px;
  }

  .table-responsive::-webkit-scrollbar-thumb {
      background-color: rgba(0, 0, 0, .5);
      border-radius: 10px;
      border: 2px solid #ffffff;
  }

  .table-responsive::-webkit-scrollbar-track {
      border-radius: 10px;  
      background-color: #ffffff; 
  }

```


<br><br><br>


<br><br><br>

### 글자 

css 속성값 user-select를 none으로 설정하여 사용자의 글자 드래그를 방지할 수 있다.

``` css
.example {
  user-select: none;  /* 글씨 드래그 방지 */
}

```


<br>




### [참고] <br>
  
  *-* 미디어쿼리 min-width & max-width - https://studiomeal.com/archives/1004 <br>
  *-* 반응형 웹 레이아웃 설계방법 - https://www.samsungsds.com/kr/insights/Responsive-Web-2.html <br>

  <br>

  * 컴포넌트 레이아웃 [Layout] <br>
  *-* z-index - https://abcdqbbq.tistory.com/39 <br>
  *-* CSS float 사용방법 - https://ojji.wayful.com/2014/01/HTML-DIV-to-Float-Three-Divs-side-by-side.html <br>
  *-* float 사용 후 처리방법 [가상요소활용] - https://neul-carpediem.tistory.com/278 <br>
  *-* 가상 선택자 vs 가상요소 (:after, ::after)의 차이점 - https://coding-designer.tistory.com/30 <br>

  *-* CSS flex 사용방법 [자세함] @@@@ - https://studiomeal.com/archives/197 <br>

  * 영역내 컨텐츠 <br>

  <br>

  * **table** <br>
  *-* 테이블 스크롤(종,횡) 자동생성 방법 (예시1) - https://dailyscript.tistory.com/entry/%EB%B0%98%EC%9D%91%ED%98%95-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EA%B0%80%EB%A1%9C-%EC%8A%A4%ED%81%AC%EB%A1%A4-%ED%9A%A1%EC%8A%A4%ED%81%AC%EB%A1%A4-%EC%A0%81%EC%9A%A9-%EB%B0%A9%EB%B2%95 <br>
  *-* .table-responsive 스크롤바 보이게 하는 방법 (css 적용) [stackoverflow] @@@ - https://stackoverflow.com/questions/25777374/always-show-scrollbar-in-bootstrap-table-responsive <br>
  *-* 웹 브라우저 스크롤바 css 적용방법 - https://webisfree.com/2019-01-08/css-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-%EC%8A%A4%ED%81%AC%EB%A1%A4%EB%B0%94-%EC%8A%A4%ED%83%80%EC%9D%BC-%EC%A7%80%EC%A0%95-%EB%B0%94%EA%BE%B8%EB%8A%94-%EB%B0%A9%EB%B2%95-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0 <br>


  *-* 글자(폰트) 그림자 - https://mintaku.tistory.com/27 <br>

