# DOM 트리 제어 

## Element 생성, 추가, 선택, 제거
---

### **요소 탐색**
* 상위 요소 : Element.closest(selectors)
* 하위 요소 : 
* 형제 요소 : 
* 기타..

<br>

## Element 조작
---
<br>

### 공통 속성 특징
---
<br>

**데이터 속성 사용하기** <br>
difference ->  $().data() vs Element.dataset

<br>

**Element.ClassList**


<br>

### Element별 속성 특징

**input**

focus()를 사용시 커서가 제일 끝에 오게 하는 방법 (아래 코드 참고) - setSelectionRange() 함수  <br>

``` javascript
  function focusAtLast(selector) {
    var input = document.querySelector(selector);
    var length = input.value.length;
    
    input.focus();
    input.setSelectionRange(length, length)
  }

```


**Select, Radio, CheckBox**

<br>


[참고] - jQuery
``` javascript /* jQuery 예시 */
/********** value **********/
$(선택자).val(); //value값 가져오기
$("#id").val(); //id로 접근하여 value가져오기
$("select[속성='속성명']").val(); //속성으로 접근하여 value가져오기

/********** text **********/
$(선택자 option:selected).text(); //text값 가져오기
$("#id option:selected").text();
$("select[속성='속성명'] option:selected").text();


$("select[name=location]").change(function(){
  console.log($(this).val()); //value값 가져오기
  console.log($("select[name=location] option:selected").text()); //text값 가져오기
});
```



## Event

* inline onclick vs addEventHandler
> stackflow에서는 확장성을 고려했을 때 inline보다는 addEventHandler를 사용하는 것이 더 낫다고 이야기.


### [참고]

  *-* element 추가 [mozilla] - https://developer.mozilla.org/ko/docs/Web/API/Node/appendChild <br>

  * Element 조작 <br>
  *-* $.data() vs Element.dataset (**차이점**) - https://stackoverflow.com/questions/23596751/dataset-vs-data-difference <br>
  *-* select 값 제어 - https://myhappyman.tistory.com/61 <br>
  *-* jQuery check_box, radio 제어 - https://living-only-today.tistory.com/107 <br>
  