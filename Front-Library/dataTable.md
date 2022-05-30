# dataTable

라이브러리 이해하기
1. 초기화 : 기본적인 설정방법 파악
2. 커스텀 초기화 : 설정 옵션들을 활용하여 원하는 기능에 맞추어 커스텀 진행
3. api 활용 : 제공되는 api를 통해 필요에 따라 추가적인 기능 사용

## Data


<br><br><br>

## Ajax : 'Server - side processing'
ajax를 통해 Server의 DB에 접근하여 데이터를 가져와 테이블을 생성가능
> check: *DataTables > Manual > Server-side processing* 

<br>

[주요옵션]
* **serverSide** : server-side 작업을 위해 필요한 옵션 (대소문자를 틀리면 인식못함)
* **ajax** : server-side 작업을 위해 필요한 옵션
* processing : 데이터 렌더링이 완료될 때까지 진행중임을 표시하는 UI 제공
  *>* dom 옵션에서 'r'을 추가하지 않으면 보이지 않음. <br>
  check: If the processing indicator does not show, check if you are using a custom 'dom' option. The letter 'r' represents the processing indicator so if it's not showing, that could be missing. See https://datatables.net/reference/option/dom
* columns : 컬럼 값 지정 및 관련 옵션 설정
* columnDefs : 컬럼 값 지정 및 관련 옵션 설정 - column을 확장한 옵션이라고 생각할 수 있다. (column에서 사용하는 하위 옵션들 사용 가능)
  (choose one of them above [columns, columnDefs])
* columnDefs.targets

  - 테이블 각 행의 번호를 오름차순 or 내림차순으로 설정할 때 render 옵션을 활용
    > meta 인자 값을 살펴보면 해당 기능을 쉽게 구현가능

  ``` javascript
  {
    "data": "id",
    render: function (data, type, row, meta) {
        var totalCount = meta.settings.json.recordsTotal
				return totalCount - meta.row;
    }
  }

  ```

<br><br><br>

[기본옵션]
* pageLength : 화면에 표시될 테이블 행(row)의 개수 (관련 옵션: **lengthMenu**, lengthChange)
  > 기본값이 10이기 때문에 lengthMenu 없이 커스텀 lengthMenu를 만들고 다른 기본값을 사용할 경우 따로 설정해주어야 한다.


  eg) 5, 10, 15로 선택할 수 있게 하려고 했을 때 의도치 않은 pagination이 발생

* lengthMenu : 화면에 표시될 테이블 행(row)의 개수 리스트
  > lengthMenu 숫자 배열의 첫번째 값이 자동으로 pageLength값으로 설정되기 때문에 lengthMenu 사용시 pageLength를 지정할 필요가 없음.

Server에서 'draw', 'recordsTotal', 'recordsFiltered', 'data'를 전달하면 dataSrc를 수정할 필요가 없다.



<br><br><br>
<br><br><br>
<br><br><br>

## DataTable api

Datatable은 데이터테이블을 생성하고 난 다음 (초기화 이후) 테이블에 접근하여 데이터를 수정할 수 있는 api 를 제공한다.


<br>

### row

* rows() : 데이터테이블에서 원하는 행을 선택하도록 지원하는 api.
  rows([modifier])
  rows(rowSelector[, modifier])
  > 아래 예시 처럼 rows() api에 row 엘리먼트(selector)를 넣으면 DataTable에서 해당 행의 데이터를 얻거나 조작할 수 있다.



<br>

``` javascript

/*
 * rowSelector 예시.
 */
var tableA = $('#tableA').DataTable({
  // ...
});

$('#anonymousDiv').on('click', function() {
  var row = $(this).closest('tr');

  var tableRow = tableA.rows(row).data();
});



```




<br><br><br>


## Exception Handling

callback 함수 (or listener)를 통해 빠르게 DataTables의 생성 및 재생성이 요청될 경우 아래와 같은 예외가 발생할 수 있다.

> jquery.dataTables.min.js:137 Uncaught TypeError: Cannot read property 'parentNode' of null

테이블의 destroy / clear / draw 작업의 속도가 메서드의 호출 속도를 못따라가기 때문인 것으로 보인다.







<br><br><br>
<br><br><br>
<br><br><br>

## Events


## css

x축 스크롤바

대상이 되는 테이블에 'width: 100%'를 주면 테이블이 생성되며 밑에 스크롤바가 생기는 현상을 막을 수 있음. (*Using DataTables* - Examples > Basic initialisation)


column 길이 변동

table-layout 속성값을 fixed로 설정하면 데이터가 길어서 지정한 너비 이상으로 셀을 미는 것을 방지할 수 있다.


<br><br>

### [참고] <br>
  
  * *Official site*
  
  *-* *DataTable Official Document* - https://datatables.net/manual/ <br>
  *-* dataTable 설정 옵션 정보 [Official] - https://datatables.net/reference/option/ <br>
  *-* Server-side processing **parameters** (send / return ~ 전달 파라미터) - https://datatables.net/manual/server-side#Returned-data <br>
  *-* Server-side process example - https://datatables.net/examples/server_side/simple.html <br>

  *-* youtube video - https://youtu.be/0FQkioPkl7I <br>
  *-* dataTable 기본 옵션 정보 블로그 - https://nomoneynohappy.tistory.com/31 <br>
  *-* 테이블 행 번호 매기기 - https://stackoverflow.com/questions/6871198/add-row-number-column-to-jquery-datatables <br>

  *-* dataTable server-side 블로그 - https://www.leafcats.com/63 <br>
  *-* dataTable server-side 블로그 2 - https://velog.io/@alstjd8826/TIL-jQuery-Bootstrap-Ajax-dataTable-pagination-search-sort <br>
  *-* dataTable server-side 블로그 3 - https://zamezzz.tistory.com/310 <br>

  *-* lengthMenu 참고 - https://stackoverflow.com/questions/8051302/jquery-datatables-pagination-size <br>

  <br>
  
  * DataTable api <br>
  *-* rows() 활용 방식 (질문자의 소스코드 참고) - https://datatables.net/forums/discussion/55277/editor-modifier-clicking-an-element-within-a-cell <br>
  
  <br>

  * Event processing <br>
  *-* dataTable events (페이지 로드 때마다 event를 넣기 위해 참고) - https://mail.datatables.net/reference/event/#buttons <br>

  <br>

  * Exception handling <br>
  *-* cannot read property 'pareentNode' of null (dataTables) - https://datatables.net/forums/discussion/48716/cannot-read-property-parentnode-of-null <br>

  <br>

  * CSS
  *-* table-layout: fixed (너비 고정) - https://jowook.tistory.com/entry/table%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-tablelayout-%EC%86%8D%EC%84%B1%EC%9C%BC%EB%A1%9C-%EB%84%88%EB%B9%84-%EA%B3%A0%EC%A0%95%ED%95%98%EA%B8%B0 <br>
