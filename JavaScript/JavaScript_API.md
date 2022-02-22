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

## Object

* 프로퍼티 접근방법 (Accessing Object Properties)
  * **dot notation** : objectName.propertyName
  * **bracket notation** : objectName["propertyName"]

<br>

> bracket은 프로퍼티가 숫자, 기호등으로 표현되어있을 때 사용 가능
> 하지만, 관습적으로 필드명은 영문자로 표현하기 때문에 도트 표기법을 주로 사용


## String
> String.prototype.method()

<br>

* String.slice(beginIndex[, endIndex]) : 문자열의 일부를 추출하면서 새로운 문자열을 반환
  * beginIndex가 음수라면 'beginIndex = strLength(문자열 길이) + beginIndex'로 처리
  e.g.) beginIndex가 -3이면 시작점은 strLength-3이 된다.
  * 한자리로 나오는 Date객체의 getDate() or getMonth()를 두 자리로 바꾸어 표현 가능
  ``` javascript
  var today = new Date(); 
  var formattedDate = ('00' + today.getDate()).slice(-2);
  ```



<br>

## 함수 표기법

* 일반함수 vs 화살표 함수
  > 'function' vs '() => '


<br>

## Array
> Array.prototype.method() - 편의를 위해 prototype 생략 후 표기

<br>

* Array.push(element) : 배열의 끝에 요소 추가, 배열의 새로운 length 속성값 반환
* Array.pop() : 배열에서 마지막 요소를 제거하고 그 요소를 반환
* Array.unshift() : 배열의 맨 앞에 하나 이상의 요소를 추가, 배열의 변경된 length 속성값 반환
* Array.at(index) : index에 위치한 요소 반환, 대괄호([]) 대신 사용가능 (대괄호를 사용해도 상관없다.)
  * '-1'을 사용하여 맨 마지막 요소를 가져올 수 있다. (최근에 생긴 메소드이기 때문에 대괄호를 사용하는 것이 더 바람직해 보인다.)
* Array.find(e => e > number) : 주어진 판별 함수를 만족하는 첫 번째 요소 값을 반환 (존재하지 않으면 undefined를 반환)
* Array.findIndex(e => e > number) : 주어진 판별 함수를 만족하는 첫 번째 요소의 인덱스를 반환 (존재하지 않으면 -1을 반환)
* Array.sort([compareFunction]) : 배열을 정렬한 후 반환 (원배열이 정렬 - 복사본 X)
  * compareFunction : 정렬 순서를 정의하는 함수. 생략하면 각 요소의 유니코드 값에 따라 정렬 
* Array.forEach(callback(currentElement[, index[, array]])) : 주어진 함수를 배열 요소 각각에 대해 실행 [cf. for-loop]
* Array.toString() : 배열을 표현하는 문자열 반환 (배열을 합쳐 콤마로 구분)
* Array.join([seperator]) : 배열의 모든 요소를 연결해 하나의 문자열로 반환
  (매개변수가 없으면 toString()과 같지만 인수로 seperator를 지정할 수 있음)

<br><br>

## Web API
Window.localStorage
* setItem(key, value)
* getItem(key)
* removeItem(key)
* clear();


global method
* setTimeout() : 호출 뒤 지정한 콜백함수를 실행하는 타이머 설정
* clearTimeout() : 
* setInterval() 


## JSON
> JSON(JavaScript Object Notation) : 자바스크립트 객체 표기법에서 유래되었으나 JSON format은 text를 의미. (객체가 아니다.)

* JSON.parse(text) : to convert the string into a JavaScript object.
* JSON.stringify(object) : to convert an object into a JSON string.

<br><br>

## 정규표현식
---
<br>

만드는 방법

* 정규식 리터럴

``` javascript
  var regex = /^[0-9]{5}$/;  // 숫자 5자리

```

* RegExp 객체의 생성자 함수

``` javascript
  var regex = new RegExp("^[0-9]{5}$");  // mozila 예시: var re = new RegExp("ab+c");

```

<br><br>

## ?

await - await연산자는 Promise를 기다리기 위해 사용되며 연산자는 async function 내부에서만 사용가능
async function - 비동기 함수
Promise - Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타냄



<br><br><br><br>

### [참고] <br>
  *-* **Mozilla** (모질라) - https://developer.mozilla.org/ko/ <br>

  *-* String > slice() 참고 (Date) - https://mitny.github.io/articles/2019-07/JS-Date-0d <br>

  *-* Mozilla > Array - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array <br>
  *-* Array at(idx) vs [idx] in JS - https://stackoverflow.com/questions/70456996/using-array-atindex-instead-of-arrayindex-in-javascript <br>
  *-* 프로퍼티 접근 방식 비교 dot vs bracket - https://stackoverflow.com/questions/17189642/difference-between-using-bracket-and-dot-notation <br>

  *-* Mozilla > localStorage - https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage <br>

  \<**W3 school**> <br>
  *-* JS JSON - https://www.w3schools.com/js/js_json.asp <br>
  *-* JSON tutorial - https://www.w3schools.com/js/js_json_intro.asp <br>

  *-* 정규표현식 (official) - https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_Expressions#special-negated-character-set <br>
  *-* 정규표현식 (블로그설명) - https://fabric004.tistory.com/20 <br>

  