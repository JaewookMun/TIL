# MessageSource

## **MessageSource** : 웹사이트의 다국어 지원기능을 구현하는데 도움을 주는 인터페이스
  (국제화 - i18n)

<br>

**사용법**

1. .properties 파일 생성
   
   *-* [파일이름]*_*[언어]*_*[국가].properties 형태로 메세지를 설정하기 위한 파일을 추가
   (파일 이름에 국가를 생략하고 만들어도 문제가 발생하지는 않는다.)
   *-* key=value 형식으로 값 입력
   <br>
   ``` properties
   # Example

   validation.name=이름을 입력해 주세요.
   ```


<br>

2. bean 등록 - MessageSource 구현체
   <br>
   
   ``` java
   // Java Configuration
   ```

   ``` xml
   <!-- XML Configuration -->
   ```

<br>


3. 출력 확인
   
  

<br>

## arguments 사용하기

* properties 파일에서 {}를 사용해 인수가 들어갈 자리 표현
* spring:message 에서 arguments를 선언하고 arguments로 선언한 코드를 replace하여 동적인 문구를 생성 가능



<br><br>

* [참고]
  *-* spring message(다국어 지원기능 사용) - https://engkimbs.tistory.com/717 <br>
  *-* 동적인 spring message 사용하기 [arguments] - https://lookingfor.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C-springmessage%EC%97%90-arguments-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95 <br>

