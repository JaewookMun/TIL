# jQuery

## Element 생성, 추가, 선택, 제거
---

### **요소 탐색**
* 상위 요소 : parent(), closest(selector)
* 하위 요소 : find(selector)
* 형제 요소 : siblings(selector)
* 기타..

<br><br>

## Element 조작

* .prop() vs .attr()

<br><br>

## Input tag

* CheckBox 전체 선택 (속성 설정 - checked )
  
``` javascript
  // 전체 선택
  $('선택자').on('click', function(){
      if($('단일 선택자').is(':checked')) $('복수 선택자').prop('checked', true);
      else $('선택자').prop('checked', false);
  });

  // 모두 선택 시 전체선택 설정
  $('복수 선택자').on('click', function(){
      var total = $('복수 선택자').length;
      var checked = $('복수 선택자:checked').length;

      if(total != checked) $('단일 선택자').prop('checked', false);
      else $('단일 선택자').prop('checked', true);
  });


```

<br><br>

## Modal

  * $('#modalID').modal('show') : 열기
  * $('#modalID').modal('hide') : 닫기
  * $('#modalID').on('hidden.bs.modal', function (e) {}) : modal 종료 시, 이벤트 처리
  * $('#modalID').off() : modal 종료 시, 이벤트 처리 해제
  * $('#modalID').on('shown.bs.modal', function (e) {}) : modal 오픈 시, 이벤트 처리
  * 





<br><br><br><br>

### [참고] <br>
  * Element Create, Read, Delete <br>
  *-* **요소의 탐색** [입문] - http://www.devkuma.com/books/pages/220 <br>

  <br>

  * Element Update <br>
  *-* difference? .prop() vs .attr() - https://stackoverflow.com/questions/13247058/jquery-attr-vs-prop <br>
  *-* checkbox 전체 선택 - https://drcode-devblog.tistory.com/217 <br>
  *-* jQuery modal 창 제어 - https://iruplace.tistory.com/235 <br>

  *-* difference? .on('click') vs .click() - https://stackoverflow.com/questions/9122078/difference-between-onclick-vs-click <br>