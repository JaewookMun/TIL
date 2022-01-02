## Spring Security

* **Architecture**

  ![Alt text](./images/spring_security_authentication_architecture.png)

<br>

* Spring Security Configuration
  
  <br>

  ``` xml
  <- web.xml ->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>
      /WEB-INF/spring/root-context.xml
      /WEB-INF/spring/security-context.xml
    </param-value>
  </context-param>

  ```
  *-* 위처럼 param-value 태그 안에 security 설정정보(security-context)를 넣지 않으면 security-context.xml에서 root-context.xml에 있는 bean 정보를 읽지 못한다.

  ``` xml
  <- 예) 잘못된 설정 ->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/spring/root-context.xml</param-value>
    <param-value>/WEB-INF/spring/security-context.xml</param-value>
  </context-param>

  ```


<br>


* authentication provider
  
  - PasswordEncoder : 비밀번호 단방향 암호화 지원
    *-* BcryptPasswordEncoder 
    *-* Argon2PasswordEncoder 
    *-* Pbkdf2PasswordEncoder 
    *-* SCryptPasswordEncoder 

<br>

* session management
  - HttpSessionEventPublisher vs HttpSessionListener

  
<br>



* Spring boot 버전2 부터는 JDK 11 이상 사용을 권장

<br>

* [참고]
  * with SpringBoot<br>
  *-* 스프링 시큐리티 프로젝트 시리즈 - https://blog.naver.com/jieuni4u/221804008187<br>
  
  * with legacy Spring<br>
  *-* **스프링 시큐리티 프로젝트 설정** - https://sjh836.tistory.com/165<br>
  *-* 스프링 시큐리티 프로젝트 설정 - https://bin-repository.tistory.com/128   (springboot에 가까운 느낌)
  *-* PasswordEncoder - https://velog.io/@corgi/Spring-Security-PasswordEncoder%EB%9E%80-4kkyw8gi<br>
  *-* logout success handler - https://tyson.tistory.com/126<br>
  *-* **session 종료관련 리스너** - https://stackoverflow.com/questions/11843010/logout-session-timeout-catching-with-spring-security<br>
  *-* 중복 로그인 방지(with security vs without security) - http://dveamer.github.io/backend/PreventDuplicatedLogin.html<br>
  *-* session timeout 설정방법 및 우선순위 - https://dololak.tistory.com/706<br>

