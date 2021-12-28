## MessageSource

* **MessageSource** : 웹사이트의 다국어 지원기능을 구현하는데 도움을 주는 인터페이스
  (국제화 - i18n)

<br>

* **사용법**

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

* [참고]
  *-* https://engkimbs.tistory.com/717

