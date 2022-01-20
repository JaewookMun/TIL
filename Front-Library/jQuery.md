# jQuery


<br>

## Input tag

* CheckBox 전체 선택
  
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


## Modal

  * $('#modalID').modal('show') : 열기
  * $('#modalID').modal('hide') : 닫기
  * $('#modalID').on('hidden.bs.modal', function (e) {}) : modal 종료 시, 이벤트 처리
  * $('#modalID').off() : modal 종료 시, 이벤트 처리 해제
  * $('#modalID').on('shown.bs.modal', function (e) {}) : modal 오픈 시, 이벤트 처리
  * 





<br>

### [참고] <br>
  *-* jQuery 전체 선택 - https://drcode-devblog.tistory.com/217 <br>

  *-* jQuery modal 창 제어 - https://iruplace.tistory.com/235 <br>