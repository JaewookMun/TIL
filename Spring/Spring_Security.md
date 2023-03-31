# Spring Security

<br>

## 개념 - 용어 정리






<br><br>

## **Architecture**

  ![Alt text](./images/spring_security_authentication_architecture.png)

<br>

<br><br>

## **Authentication and Access Control (Authorization)**
---


Application Security를 위해 중요한 개념은 크게 인증(Authentication)과 인가(Authorization)이다. 
Spring Security는 두 개념을 분리한 뒤 기능을 확장한 구조를 가진다.

* authentication : who are you?
* authorization (or access control) : what are you allowed to do? 

<br><br>

### **Authentication**

Authentication의 중요 인터페이스는 **AuthenticationManager**이며 하나의 메서드(authenticate())를 갖는다.

``` java 
public interface AuthenticationManager {
  Authentication authenticate(Authentication authentication) throws AuthenticationException
}

```


<br>

AuthenticationManager의 기능
1. Authentication 반환 (유효한 사용자 정보가 입력되었다면 authenticated = true 상태)
2. 입력값이 적합하지 않으면 AuthenticationException 발생
3. 확정할 수 없다면 null 반환


<br><br>

AuthenticationManager의 구현

* 구현체 : **ProviderManager**
* 특징 : AuthenticationProvider 인스턴스들을 사용*  <br>
  (Authentication 인스턴스의 타입을 특정하여 알맞는 AuthenticationProvider 인스턴스를 사용) <br>
  (*: AuthenticationProvider 인스턴스 체인에 위임)


<br><br>

AuthenticationManager 설정 




<br><br><br>





## Spring Security Configuration

0. 라이브러리 추가 (dependencies)

1. web.xml 설정

레거시 프로젝트는 web.xml에 스프링 빈 등록을 위한 설정정보를 작성해야한다. (Spring Security 관련 bean 설정정보 파일)

  <br>

  ``` xml
  <- web.xml - (1) ->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>
      /WEB-INF/spring/root-context.xml
      /WEB-INF/spring/security-context.xml
    </param-value>
  </context-param>
  
  <- web.xml - (2) ->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>
      com.security.session.config.AppConfig
			com.security.session.config.WebSecurityConfig
    </param-value>
  </context-param>

  ...

  <filter>
		<filter-name>springSecurityFilterChain</filter-name>
		<filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
	</filter>
	<filter-mapping>
		<filter-name>springSecurityFilterChain</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>

  ```
  *-* 위처럼 param-value 태그 안에 security 설정정보(security-context)를 넣지 않으면 security-context.xml에서 root-context.xml에 있는 bean 정보를 읽지 못한다. <br>
  *-* AnnotationConfigApplicationContext를 활용해서 Java Configuration을 할 때도 security 설정 클래스를 param-value에 함께 넣어준다. <br>
  *-* DelegatingFilterProxy 등록 <br>
      (스프링 부트와 달리 기존 스프링 프레임워크에서 DelegatingFilterProxy를 등록하지 않으면 spring security 기능을 적용할 수 없다.)

  <br>

  ``` xml
  <- 예) 잘못된 설정 ->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/spring/root-context.xml</param-value>
    <param-value>/WEB-INF/spring/security-context.xml</param-value>
  </context-param>

  ```

<br>

## SecurityContext

SecurityContext 가져오기 - 2가지 방법 존재 <br>

* SecurityContextHolder
* HttpSession


``` java
  SecurityContext securityContext = SecurityContextHolder.getContext();

  Object securityContextObject = session.getAttribute(HttpSessionSecurityContextRepository.SPRING_SECURITY_CONTEXT_KEY);
  if(securityContextObject != null){ 
    SecurityContext securityContext = (SecurityContext)securityContextObject;
  }



```


<br><br>


## AuthenticationManager
  * 구현체 <br>
  *-* ProviderManager

<br><br>

## AuthenticationProvider
---
<br>
회원 로그인 작업 관리 - 아이디 조회 및 비밀번호 매칭 
> UserDetailsService, PasswordEncoder


<br>
  
### UserDetailsService : DB에서 회원정보를 가져와 저장

UserDetails 인터페이스 구현체를 반환하는데, 커스텀으로 구현한 UserDetails 구현체를 사용할 경우 equals()와 hashCode() 메서드 또한 구현해주어야 한다.

<br>

### PasswordEncoder : 비밀번호 단방향 암호화 지원
  
  * PasswordEncoder의 구현체 및 암호화 알고리즘 <br>
    *-* BcryptPasswordEncoder : bcrypt <br>
    *-* Argon2PasswordEncoder :  <br>
    *-* Pbkdf2PasswordEncoder : pbkdf2 <br>
    *-* SCryptPasswordEncoder : scrypt <br>

  * SHA-256 vs Bcrypt

<br>

  * 주요 메소드 <br>
    *-* encode(CharSequence rawPassword) : <br>
    *-* matches(CharSequence rawPassword, String encodedPassword) : <br>

<br>


<br><br><br>

## session management
---

<br>

### SessionManagementFilter, SessionAuthenticationStrategy


// AuthenticationStrategy 타입으로 빈을 읽었을 때 스프링 컨테이너에서 조회되는 빈
name: org.springframework.security.web.authentication.session.CompositeSessionAuthenticationStrategy#0, 
bean: org.springframework.security.web.authentication.session.CompositeSessionAuthenticationStrategy 
[delegateStrategies = 
  [
    org.springframework.security.web.authentication.session.ConcurrentSessionControlAuthenticationStrategy@43f61afb,
    org.springframework.security.web.authentication.session.SessionFixationProtectionStrategy@713064e8,
    org.springframework.security.web.authentication.session.RegisterSessionAuthenticationStrategy@4fad6218
  ]
]


<br>

  - HttpSessionEventPublisher vs HttpSessionListener

  
<br>

<br><br><br>

## JSTL
> JSP 정규표현식 (JavaServer Pages Standard Tag Library)

<br>

> JavaScript에서 인가된 사용자 정보 사용하기
* authentication, authorize 에서 'var'속성을 이용
``` jsp
<sec:authentication property="principal.userId" var="userId"/>
<sec:authorize access="hasRole('MASTER')" var="isMaster"></sec:authorize>

<script type="text/javascript">
  var userId = ${userId};

  if(${isMaster}) {
    console.log('this is an user having master authority');
  }


</script>

```



Q: check > https://velog.io/@devsh/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0-%EC%84%B8%EC%85%98-Session-Management-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95-%EA%B0%9C%EB%85%90-%EC%9D%B5%ED%9E%88%EA%B8%B0 <br>
https://docs.spring.io/spring-session/docs/2.2.x/reference/html/spring-security.html <br>

<br>

Q 중복 로그인 방지 ? - https://medium.com/@leejungmin03/spring-%EC%A4%91%EB%B3%B5%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EB%B0%A9%EC%A7%80-9ef32f7e7110 <br>
<br>

중복 로그인 방지 ? 2 - https://kangwoojin.github.io/programing/spring-security-basic-session-management-filter/ <br>
중복 로그인 방지 ? 3 - https://lts0606.tistory.com/320 <br>

스프링 시큐리티 로그인 시리즈 - https://codevang.tistory.com/266 <br>

세션과 인증정보 수정 - https://misoin.tistory.com/60 <br>



* Spring boot 버전2 부터는 JDK 11 이상 사용을 권장


<br>

#### [참고]

  * **Spring.io - Security references** <br>
  *-* security guid step-1 in-memory [document] - https://spring.io/guides/gs/securing-web/ <br>
  *-* security guid step-2 architecture [document] - https://spring.io/guides/topicals/spring-security-architecture/ <br>
  *-* Security Reference > Session Management [official] - https://docs.spring.io/spring-security/reference/servlet/authentication/session-management.html <br>

  *-* 스프링 시큐리티 세션이란? (blog) - https://velog.io/@devsh/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0-%EC%84%B8%EC%85%98-Session-Management-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95-%EA%B0%9C%EB%85%90-%EC%9D%B5%ED%9E%88%EA%B8%B0 <br>



  *-* delegation 이란? [delegation_pattern] - https://hashcode.co.kr/questions/6881/delegation%EC%9D%B4-%EC%9A%B0%EB%A6%AC%EB%A7%90%EB%A1%9C-%ED%95%B4%EC%84%9D%ED%95%98%EB%A9%B4-%EC%96%B4%EB%96%A4-%EB%8B%A8%EC%96%B4%EC%9D%B8%EA%B0%80%EC%9A%94 <br>


  *-* DelegatingFilterProxy  - https://velog.io/@yaho1024/spring-security-delegatingFilterProxy <br>
  *-* NoSuchBeanDefinitionException: No bean named 'springSecurityFilterChain' is defined 오류 해결 - https://haenny.tistory.com/224 <br>

  *-* SecurityContext 얻는법 - https://jekalmin.tistory.com/entry/spring-security-SecurityContext-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0 <br>


  *-* Spring Security 구조 (로그인 과정) - https://jeong-pro.tistory.com/205 <br>
  *-* 로그인 실패시 응답코드 - https://blog.naver.com/genycho/222446074415 <br>

  * with SpringBoot<br>
  *-* 
  
  * with legacy Spring<br>
  *-* **스프링 시큐리티 프로젝트 설정** - https://sjh836.tistory.com/165<br>
  *-* 스프링 시큐리티 프로젝트 설정 - https://bin-repository.tistory.com/128   (springboot에 가까운 느낌) <br>
  *-* **AuthenticationProvider** 개념 - https://gregor77.github.io/2021/05/18/spring-security-03/ <br>
  *-* UserDetails 구현 - https://to-dy.tistory.com/86 <br>
  *-* PasswordEncoder - https://velog.io/@corgi/Spring-Security-PasswordEncoder%EB%9E%80-4kkyw8gi<br>
  *-* PasswordEncoder official [**Spring.io**] - https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html#authentication-password-storage <br>
  *-* BCrypt 설명 (Password hashing 시 Bcrypt가 추천되는 이유 ) - https://velog.io/@kylexid/%EC%99%9C-bcrypt-%EC%95%94%ED%98%B8%ED%99%94-%EB%B0%A9%EC%8B%9D%EC%9D%B4-%EC%B6%94%EC%B2%9C%EB%90%98%EC%96%B4%EC%A7%88%EA%B9%8C <br>

  *-* Flash Attribute and AuthenticationFailureHandler [stackOverflow] - https://stackoverflow.com/questions/23844546/flash-attribute-in-custom-authenticationfailurehandler/50429613 <br>

  *-* logout success handler - https://tyson.tistory.com/126<br>
  *-* **session 종료관련 리스너** - https://stackoverflow.com/questions/11843010/logout-session-timeout-catching-with-spring-security<br>
  *-* 중복 로그인 방지(with security vs without security) - http://dveamer.github.io/backend/PreventDuplicatedLogin.html<br>
  *-* session timeout 설정방법 및 우선순위 - https://dololak.tistory.com/706<br>
  *-* 세션 저장소를 이용하는 3가지 방법 - https://parkadd.tistory.com/16 <br>

  *-* JSP에서 spring security 활용 - https://niees.tistory.com/19 <br>

  *-* CSRF token not found error solutions - https://stackoverflow.com/questions/28138864/expected-csrf-token-not-found-has-your-session-expired-403 <br>

  * JSTL <br>
  *-* 인증된 사용자 정보 읽기 - https://taetae0079.tistory.com/6 <br>
  *-* 시큐리티 JS에서 활용하기 - https://stackoverflow.com/questions/30775001/springsecurity-role-check-inside-javascript <br>

  * JWT
  *-* Spring session & JWT [Web 기본] - https://brunch.co.kr/@springboot/491 <br>
  *-* spring security & jwt login - https://velog.io/@shinmj1207/Spring-Spring-Security-JWT-%EB%A1%9C%EA%B7%B8%EC%9D%B8 <br>
  


