# Vanilla JavaScript

## 변수 선언

* var
* let
* const



<br>

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



<br><br>

## 함수 표기법
<br>

가변인자 함수 - arguments 객체
--

Q: 다중 파라미터 vs 가변인자 함수



<br><br>

일반함수 vs 화살표 함수
--

> 'function' vs '() => '




<br><br>

## **자바스크립트 객체 (Object)**

구성 요소
* 생성자(constructor)
* 프로퍼티 (static / instance)
* 메서드 (static / instance)

<br>

프로퍼티 접근방법 (Accessing Object Properties)
* **dot notation** : objectName.propertyName
* **bracket notation** : objectName["propertyName"]

<br>

> bracket은 프로퍼티가 숫자, 기호등으로 표현되어있을 때 사용 가능
> 하지만, 관습적으로 필드명은 영문자로 표현하기 때문에 도트 표기법을 주로 사용





<br>



<br><br>

## **표준 내장 객체 (Standard built-in objects)**
---

표준 내장 객체와 전역 객체를 헷갈리지 않도록 주의하는 것이 필요.
-> 전역객체란?


<br>

## Object

Static methods

* Object.keys(obj) : 주어진 객체의 속성 이름에 해당하는 문자열들을 배열로 반환
* Object.entries(obj) : 



<br>

Instance methods




<br><br>

## String
> String.prototype.method()

<br>

* String.slice(beginIndex[, endIndex]) : 문자열의 일부를 추출하면서 새로운 문자열을 반환
  - beginIndex가 음수라면 'beginIndex = strLength(문자열 길이) + beginIndex'로 처리
  e.g.) beginIndex가 -3이면 시작점은 strLength-3이 된다.
  - 한자리로 나오는 Date객체의 getDate() or getMonth()를 두 자리로 바꾸어 표현 가능
  
  ``` javascript
  var today = new Date(); 
  var formattedDate = ('00' + today.getDate()).slice(-2);
  ```
  <br>

* String.indexOf(searchValue) : 호출한 String 객체에서 주어진 값과 일치하는 첫 번째 인덱스를 반환 (일치 값이 없으면 -1 반환)
* String.includes(searchString) : 하나의 문자열이 다른 문자열에 포함되어 있는지를 판별 (true or false 반환)

  <br>
  [비고]: 주어진 String에서 다른 문자열을 찾을 때 어떤 메서드가 더 빠른가? -> indexOf() [the fastest way to find substring from a string in JS]




<br><br><br>
<br><br><br>

## Array

<br>

**Instance methods**  (편의를 위해 prototype 생략) eg. Array.prototype.method()

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

<br>


## Date

Static methods
* Date.now()

<br>

Instance methods

* date.getTime() : 표준시에 따라 지정된 날짜의 시간에 해당하는 숫자 값을 반환 (밀리초, ms) <br>
  -> 1970년 1월 1일 00:00:00 UTC에서 경과한 시간을 밀리초로 표현
  -> valueOf()와 기능적으로 동일



<br><br>

**Global 객체(?)**

## Window

onkeydown 에 함수를 연결하여 새로고침을 누를 시 GET 파라미터(쿼리스트링)을 제거할 수 있음


<br>

**Location**

window.location 객체는 현재 웹페이지 주소 (URL)을 얻거나 새로운 페이지로 리다이렉트(Redirect) 이동을 위해 사용 가능
> The window.location object can be written without the window prefix.
> eg) window.location = location

some example
* window.location.href : 현재페이지의 href (URL) 반환
* window.location.hostname : 웹 호스트의 도메인 이름 반환
* window.location.pathname : 현재 페이지의 경로 및 파일 이름 반환 (쿼리스트링은 포함되지 않음)
* window.location.protocol : 웹 프로토콜 반환 (http: or https:)
* window.location.assign() : 새로운 문서 로드


<br><br><br>

## **Web API**
---
<br>

브라우저에 데이터를 저장하는 방법 - Cookie, Storage
--
Cookie와 Storage(localStorage, sessionStorage) 모두 데이터베이스를 사용하지 않고 데이터를 임시적인 용도로 저장할 때 사용한다.
[참고]: 객체를 JSON 오브젝트를 활용해 스토리지에 저장할 수 있지만 객체에 설정한 함수는 저장할 수 없다. (객체의 필드속성만 저장가능하며 저장할 때 모두 문자처리)



<br><br>


## Cookie

Document.cookie
웹페이지에 저장된 쿠키를 문자열 형태로 읽음 (세미콜론으로 구분되는 모든 쿠키 리스트의 문자열)
> Document.cookie = *newCookie*

<br>

newCookie는 key=value 형태의 문자열로 생성하고자 하는 쿠키의 정보를 표기한다.

``` javascript
  
  Document.cookie = 'name=value;...name=value; expires=date-in-GMTString-format'
  // 쿠키의 자동 소멸시간 설정을 위해 Date 객체의 toUTCString() 사용

```

쿠키는 제거하기 위해서 만료시간을 마이너스(이전의 날짜)로 바꾸어 자동 소멸시킨다.

<br><br>

## LocalStorage

Window.localStorage
* setItem(key, value)
* getItem(key)
* removeItem(key)
* clear();

<br><br>

## SessionStorage



<br><br>

## global method
* setTimeout() : 호출 뒤 지정한 콜백함수를 실행하는 타이머 설정
* clearTimeout() : 
* setInterval() 

<br>



## JSON
> JSON(JavaScript Object Notation) : 자바스크립트 객체 표기법에서 유래되었으나 JSON format은 text를 의미. (객체가 아니다.)

* JSON.parse(text) : to convert the string into a JavaScript object.
* JSON.stringify(object) : to convert an object into a JSON string.






<br><br>

## 정규표현식 (RegExp)
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


Instance Methods

* regExp.test(string) : string이 주어진 패턴에 부합하는지 확인
  > reg.test() 가 String.match() 보다 더 빠른 참거짓 값을 반환


<br><br>

## ?

await - await연산자는 Promise를 기다리기 위해 사용되며 연산자는 async function 내부에서만 사용가능
async function - 비동기 함수
Promise - Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타냄



<br><br><br><br>

### [참고] <br>

  *-* **Mozilla** (모질라) - https://developer.mozilla.org/ko/ <br>

  *-* JS 변수 선언 [const] - https://hyunseob.github.io/2016/11/21/misunderstanding-about-const/ <br>
  *-* JS 변수 선언관련 특징 비교 블로그 - https://velog.io/@bathingape/JavaScript-var-let-const-%EC%B0%A8%EC%9D%B4%EC%A0%90 <br>

  <br>

  **함수** <br>
  *-* 가변인자 함수 (블로그) - https://jungpaeng.tistory.com/80 <br>
  *-* 여러 파라미터값 전달 (블로그) - https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=mrkanghyun&logNo=220722559377 <br>
  *-* JS 나눗셈 몫 구하기 [parseInt()] - http://blog.cloudsys.co.kr/javascript-division-result-remainder/ <br>
  *-* js 문자열 뒤집기 함수 참고 - https://dev-note-97.tistory.com/280 <br>

  <br>

  **표준 내장 객체** <br>
  *-* String > slice() 참고 (Date) - https://mitny.github.io/articles/2019-07/JS-Date-0d <br>
  *-* Fastest way to find substring from a string - https://stackoverflow.com/questions/5296268/fastest-way-to-check-a-string-contain-another-substring-in-javascript <br>


  *-* Mozilla > Array - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array <br>
  *-* Array at(idx) vs [idx] in JS - https://stackoverflow.com/questions/70456996/using-array-atindex-instead-of-arrayindex-in-javascript <br>
  *-* 프로퍼티 접근 방식 비교 dot vs bracket - https://stackoverflow.com/questions/17189642/difference-between-using-bracket-and-dot-notation <br>
  *-* GET 파라미터 제거 후 새로고침 - https://java119.tistory.com/35 <br>
  
  *-* w3 shcool > **window.location** - https://www.w3schools.com/js/js_window_location.asp <br>
  
  <br>

  **Web API** <br>
  *-* Mozilla > localStorage - https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage <br>
  *-* cookie, session의 차이 (블로그) - https://hahahoho5915.tistory.com/32 <br>
  *-* cookie, localStorage, SessionStorage 개념 블로그(비교분석) - https://fathory.tistory.com/33 <br>
  *-* how to make cookie which expires in 5 minutes - https://stackoverflow.com/questions/45889099/javascript-make-a-cookie-expire-in-5-minutes <br>
  *-* 쿠키 이름으로 쿠키 가져오기 1 (stackoverflow) - https://stackoverflow.com/questions/10730362/get-cookie-by-name <br>
  *-* 쿠키 CRUD 기능 구현 (쿠키가져오기 2) - https://bluemint.tistory.com/6 <br>
  *-* localStorage 사용방법 (객체 저장 및 읽기) - https://goddino.tistory.com/207 <br>

  <br>

  **W3 school** <br>
  *-* JS JSON - https://www.w3schools.com/js/js_json.asp <br>
  *-* JSON tutorial - https://www.w3schools.com/js/js_json_intro.asp <br>

  *-* 정규표현식 (official) - https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_Expressions#special-negated-character-set <br>
  *-* 정규표현식 (블로그설명) - https://fabric004.tistory.com/20 <br>
  *-* regExp.test() vs string.match() - https://stackoverflow.com/questions/10940137/regex-test-v-s-string-match-to-know-if-a-string-matches-a-regular-expression <br>

  