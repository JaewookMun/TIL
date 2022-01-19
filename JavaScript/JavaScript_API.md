# Vanilla JavaScript

## undefined
> 값을 할당하지 않은 변수는 undefined 자료형이며 함수가 명시적으로 값을 반환하지 않으면 undefined를 반환한다. 
> 따라서, undefined와 일치/불일치 연산자를 사용해 변수에 값이 할당되었는지를 구분할 수 있다.

* _*_ 주의: 동등연산자가 아닌 일치연산자를 사용해야한다. 동등 연산자를 사용 시 'x == undefined' 는 x가 null일 때도 참이 되기 때문이다. -> undefined & 일치 연산자

<br>

``` javascript
    // ex1
    var x;
    if(x === undefined) {
        // 실행
    } else {
        // 실행되지 않음.
    }

    // ex2
    if(typeof x === 'undefined') {
        // 실행
    }

```
 


<br>

## Array
> Array.prototype.method() - 편의를 위해 prototype 생략 후 표기

* Array.push(element) : 배열의 끝에 요소 추가, 호출한 배열의 새로운 length 속성값 반환
* Array.pop() : 배열에서 마지막 요소를 제거하고 그 요소를 반환
* Array.at(index) : index에 위치한 요소 반환, 대괄호([]) 대신 사용가능 (대괄호를 사용해도 상관없다.)
* Array.find(e => e > number) : 주어진 판별 함수를 만족하는 첫 번째 요소 값을 반환 (존재하지 않으면 undefined를 반환)
* Array.findIndex(e => e > number) : 주어진 판별 함수를 만족하는 첫 번째 요소의 인덱스를 반환 (존재하지 않으면 -1을 반환)
* Array.sort([compareFunction]) : 배열을 정렬한 후 반환 (원배열이 정렬 - 복사본 X)
  * compareFunction : 정렬 순서를 정의하는 함수. 생략하면 각 요소의 유니코드 값에 따라 정렬 
* Array.forEach(callback(currentElement[, index[, array]])) : 주어진 함수를 배열 요소 각각에 대해 실행 [cf. for-loop]



## JSON
> JSON(JavaScript Object Notation) : 자바스크립트 객체 표기법에서 유래되었으나 JSON format은 text를 의미. (객체가 아니다.)

* JSON.parse(text) : to convert the string into a JavaScript object.
* JSON.stringify(object) : to convert an object into a JSON string.


<br>

* [참고] <br>
  *-* **Mozilla** (모질라) - https://developer.mozilla.org/ko/ <br>
  *-* Mozilla > Array - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array <br>
  
  \<**W3 school**> <br>
  *-* JS JSON - https://www.w3schools.com/js/js_json.asp <br>
  *-* JSON tutorial - https://www.w3schools.com/js/js_json_intro.asp <br>