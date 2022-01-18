# jQuery

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



* [참고]
  *-* jQuery 전체 선택 - https://drcode-devblog.tistory.com/217 <br>