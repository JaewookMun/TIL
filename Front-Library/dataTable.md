# dataTable


## Data

## Ajax

## 'Server - side processing'
ajax를 통해 Server의 DB에 접근하여 데이터를 가져와 테이블을 생성가능
> check: *DataTables > Manual > Server-side processing* 


<br>

[필요옵션]
* **serverSide** : server-side 작업을 위해 필요한 옵션 (대소문자를 틀리면 인식못함)
* **ajax** : server-side 작업을 위해 필요한 옵션
* processing : 데이터 렌더링이 완료될 때까지 진행중임을 표시하는 UI 제공
  *>* dom 옵션에서 'r'을 추가하지 않으면 보이지 않음. <br>
  check: If the processing indicator does not show, check if you are using a custom 'dom' option. The letter 'r' represents the processing indicator so if it's not showing, that could be missing. See https://datatables.net/reference/option/dom
* columns
* columnDefs
  (choose one of them above [columns, columnDefs])
* columnDefs.targets

[기본옵션]
* lengthMenu : 화면에 표시될 테이블 행(row)의 개수

Server에서 'draw', 'recordsTotal', 'recordsFiltered', 'data'를 전달하면 dataSrc를 수정할 필요가 없다.



<br>

## API


### [참고] <br>
  * *Official site*
  *-* *DataTable Official Document* - https://datatables.net/manual/ <br>
  *-* dataTable 설정 옵션 정보 [Official] - https://datatables.net/reference/option/ <br>
  *-* Server-side processing **parameters** (send / return ~ 전달 파라미터) - https://datatables.net/manual/server-side#Returned-data <br>
  *-* Server-side process example - https://datatables.net/examples/server_side/simple.html <br>

  *-* youtube video - https://youtu.be/0FQkioPkl7I <br>
  *-* dataTable 기본 옵션 정보 블로그 - https://nomoneynohappy.tistory.com/31 <br>

  *-* dataTable server-side 블로그 - https://www.leafcats.com/63 <br>
  *-* dataTable server-side 블로그 2 - https://velog.io/@alstjd8826/TIL-jQuery-Bootstrap-Ajax-dataTable-pagination-search-sort <br>
  *-* dataTable server-side 블로그 3 - https://zamezzz.tistory.com/310 <br>