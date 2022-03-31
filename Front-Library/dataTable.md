# dataTable


## Data

## Ajax

## 'Server - side processing'
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


[기본옵션]
* pageLength : 화면에 표시될 테이블 행(row)의 개수 (관련 옵션: **lengthMenu**, lengthChange)
  > 기본값이 10이기 때문에 lengthMenu 없이 커스텀 lengthMenu를 만들고 다른 기본값을 사용할 경우 따로 설정해주어야 한다.


  eg) 5, 10, 15로 선택할 수 있게 하려고 했을 때 의도치 않은 pagination이 발생

* lengthMenu : 화면에 표시될 테이블 행(row)의 개수 리스트
  > lengthMenu 숫자 배열의 첫번째 값이 자동으로 pageLength값으로 설정되기 때문에 lengthMenu 사용시 pageLength를 지정할 필요가 없음.

Server에서 'draw', 'recordsTotal', 'recordsFiltered', 'data'를 전달하면 dataSrc를 수정할 필요가 없다.



<br>

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
  *-* dataTable events (페이지 로드 때마다 event를 넣기 위해 참고) - https://mail.datatables.net/reference/event/#buttons <br>

  *-* youtube video - https://youtu.be/0FQkioPkl7I <br>
  *-* dataTable 기본 옵션 정보 블로그 - https://nomoneynohappy.tistory.com/31 <br>
  *-* 테이블 행 번호 매기기 - https://stackoverflow.com/questions/6871198/add-row-number-column-to-jquery-datatables <br>

  *-* dataTable server-side 블로그 - https://www.leafcats.com/63 <br>
  *-* dataTable server-side 블로그 2 - https://velog.io/@alstjd8826/TIL-jQuery-Bootstrap-Ajax-dataTable-pagination-search-sort <br>
  *-* dataTable server-side 블로그 3 - https://zamezzz.tistory.com/310 <br>

  *-* lengthMenu 참고 - https://stackoverflow.com/questions/8051302/jquery-datatables-pagination-size <br>

  * CSS
  
  *-* table-layout: fixed (너비 고정) - https://jowook.tistory.com/entry/table%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-tablelayout-%EC%86%8D%EC%84%B1%EC%9C%BC%EB%A1%9C-%EB%84%88%EB%B9%84-%EA%B3%A0%EC%A0%95%ED%95%98%EA%B8%B0 <br>
