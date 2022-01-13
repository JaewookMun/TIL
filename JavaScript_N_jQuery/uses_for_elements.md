# Element(엘리먼트)에 따른 DOM 조작 함수

### **Input**
#### JavaScript


#### jQuery

<br>

### **Select, Radio, CheckBox**

#### JavaScript


#### jQuery
``` javascript
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



* [참고]
  *-* jQuery check_box, radio 제어 - https://living-only-today.tistory.com/107 <br>
  *-* select 값 제어 - https://myhappyman.tistory.com/61 <br>
  

