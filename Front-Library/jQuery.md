# jQuery

## Element 생성, 추가, 선택, 제거
---

### **요소 탐색**
* 상위 요소 : parent(), closest(selector)
  > 위 두 메소드 외에 parents() 도 있지만, 위 두 메소드가 사용하기 편리
* 하위 요소 : find(selector)
* 형제 요소 : siblings(selector)
* 기타..

Q. '선택자' vs find() : 어떤게 더 빠른가?
    조건에 따라 달라지겠지만 performance 상 큰 차이는 없음 <br>


  ``` javascript
    $('#tempId h3, #tempId .tempClass')   vs   $('#tempId').find('h3')

  ```

<br>

Q. children() vs find() : 어떤게 더 빠른가? 
    performance 상 큰 차이는 없음. - find가 좀 더 빠른 것으로 생각되어짐.



<br><br>

## Element 조작

* .prop(propertyName) vs .attr(attributeName)
  * HTML 속성과 DOM 속성은 서로 다르다. (check *difference between HTML attribute and DOM property*)
  * checked, selected, or disabled와 같은 엘리먼트의 상태를 나타내는 DOM properties는 .prop() 메소드를 사용하는 것을 권장
    (jQuery 1.6 이전까지는 attr() 메소드로 property 속성값을 관리했으나 1.6 이후로 property value 값들을 관리하기 위해 .prop() 사용)

  * 즉, .attr() - 정적인 속성의 관리 /  .prop() - 동적인 속성의 관리

<br>

* .prop(propertyName) vs .is(selector) 
  * prop() 메소드는 property에 해당하는 value를 반환하고 is()는 selector에 해당하는 엘리먼트의 존재 유무를 반환한다.
    (jQuery 1.6 이후 부터는 .prop() 메소드를 사용하는 것이 좀 더 편리한 느낌)

  ``` javascript

  $.prop('checked', false); // checked propery 값을 false 로 변경 (동적 화면 구성)
  $.prop('checked'); // checked property 값을 반환 true or fasle 



  ```


<br>

**HTML 제어를 위한 API**

HTML 문서가 브라우저에 의해 load되면 브라우저는 이를 문서객체모델(DOM - Document Object Model)로 만든다.  
> we can say that the DOM is an application programming interface (API) for the HTML <br>
> HTML 문서에 접근 및 제어하기 위해 DOM이란 API를 사용한다고 생각할 수 있다.

<br>
DOM은 HTML 엘리먼트들을 객체, 객체의 프로퍼티, 메서드, 이벤트로 가지고 있다.
attribute는 HTML 문서에서 element에 대한 추가적인 정보를 제공하는 초기값이고 property는 DOM tree에서 attribute를 나타낸다고 생각할 수 있다. 때문에, DOM tree를 조작하기 위해서는(동적인 웹페이지 화면 조작) property value를 변경해야한다. (checkbox, radio, select 등등)


<br>

### difference between **HTML attribute vs DOM property**
1. The Attributes are defined by HTML whereas the properties are defined by the DOM.
2. The attribute’s main role is to initializes the DOM properties. So, once the DOM initialization complete, the attributes job is done.
3. Property values can change, whereas the attribute values can never be changed.


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
  


<br><br><br>

## Ajax

  * jquery의 ajax로 서버와 통신할 때 connection의 timeout 옵션을 주기 위해서는 asnyc 옵션을 true로 해서(default) 비동기로 통신해야한다.
  (동기통신을 사용하면 timeout 옵션을 적용할 수 없다.)
  * 동기통신처럼 ajax의 결과값을 가져와 처리하기 위해서 **Promise 객체** 사용
  * Promise 객체 - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise




<br><br><br>
<br><br><br>

## jQuery API

* $.trim() : String 앞 뒤의 공백을 잘라주는 api "        'happy birthday'     " ->   "happy birthday"



<br><br><br>
<br><br><br>
<br><br><br>

### [참고] <br>
  * Element Create, Read, Delete <br>
  *-* [jQuery] **요소 탐색** [입문] - http://www.devkuma.com/books/pages/220 <br>
  *-* ele.is(':checked') vs ele.prop('checked') [stackoverflow] - https://stackoverflow.com/questions/43464344/elem-ischecked-vs-elem-propchecked <br>
  *-* .attr() > DOM property(checked, selected, or disabled)는 .prop() 사용을 권장 - https://api.jquery.com/attr/#attr-attributeName <br>
  *-* .prop() > **Attributes vs Properties** [jQuery Doc] - https://api.jquery.com/prop/#prop-propertyName <br>
  *-* difference between HTML attribute and DOM property - https://dotnettutorials.net/lesson/html-attribute-vs-dom-property/ <br>
  *-* jQuery single selector vs .find() difference - https://stackoverflow.com/questions/6230266/jquery-single-selector-vs-find <br>
  *-* difference between children() vs find() - https://stackoverflow.com/questions/648004/what-is-fastest-children-or-find-in-jquery <br>

  <br>

  * Element Update <br>
  *-* difference? .prop() vs .attr() - https://stackoverflow.com/questions/13247058/jquery-attr-vs-prop <br>
  *-* checkbox 전체 선택 - https://drcode-devblog.tistory.com/217 <br>
  *-* jQuery modal 창 제어 - https://iruplace.tistory.com/235 <br>

  *-* difference? .on('click') vs .click() - https://stackoverflow.com/questions/9122078/difference-between-onclick-vs-click <br>

  <br>

  * Ajax
  *-* jQuery.ajax > async await 및 Promise 사용 - https://kkh0977.tistory.com/1192 <br>