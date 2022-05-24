# 스프링 (Spring)

<br>

## 스프링 설정

<br><br><br>

### Spring Legacy
---


### SpringBoot
---


<br><br><br>
<br><br><br>

Listener interface

**ServletContextListener**
: ServletContextListener를 구현한 클래스에서는 @Autowired 어노테이션을 통해 Bean을 주입받을 수 없다.

해결방법
* WebApplicationContextUtils.getWebApplicationContext(ServletContext sc) 메서드를 활용하여 WebApplicationContext를 가지고 등록된 Bean을 사용


**ApplicationListener<E extends ApplicationEvent>** 
: application event 에 대한 리스너 인터페이스

dispatcherServlet의 load 작업이 완료되었을 때 수행할 메서드를 지정할 수 있다. (dispatcherServlet 작업에 대한 콜백함수 지정)
*-*> ContextRefreshedEvent 클래스 사용

``` java
//example
@Component
public class ApplicationContextListener implements
    ApplicationListener<ContextRefreshedEvent> {

  @Override
  public void onApplicationEvent(ContextRefreshedEvent event) {
    System.out.println("dispatcherServlet was initialized or refreshed: "
        + event.getApplicationContext().getDisplayName());
  }
}

```



<br><br><br>

## Spring Dependency Injection

스프링 빈 등록 : @Bean, @Component

@Configuration 어노테이션이 붙은 클래스에 @Bean 어노테이션을 활용해 스프링 빈을 등록 가능

@Bean 어노테이션이 붙은 메서드를 작성하여 빈을 등록할 수 있으며 별도의 설정이 없다면 기본값으로 메서드 명이 빈네임이 된다. 빈 메서드의 반환 값은 빈의 상위타입으로 설정할 수 있으며 의존성을 낮추기 위해 인터페이스로 설정하는 것이 권장된다.


``` java
// example
@Configuration
public class AppConfig {

    @Bean
    public TransferService transferService() {
        return new TransferServiceImpl();
    }
}

```
<br><br>

의존성 주입 : @Bean, @Component

@Bean 어노테이션 메서드는 빈을 생성하기 위해 필요한 의존성을 갖는 임의의 객체들을 파라미터로 가질 수 있다.

추가로 @Configuration 클래스 내부에 선언된 다른 메서드를 내부에서 호출하여 의존성을 주입할 수도 있다. (inter-bean references : 빈 간의 참조)
<br>
> @Configuration 클래스 내에서 @Bean 메서드를 호출하는 bean 의존성 주입방법은 다른 @Configuration 클래스의 @Bean 메서드를 호출해도 동일하게 적용된다.

<br>

``` java
// example - spring core - Bean Dependencies
@Configuration
public class AppConfig {
    // spring.io - document
    @Bean
    public TransferService transferService(AccountRepository accountRepository) {
        return new TransferServiceImpl(accountRepository);
    }

    // custom example
    @Bean
    public RegisterService registerService() {
      returnd new RegisterServiceImpl(transferService());
    }
}

...

@Configuration
public class OtherConfig {
    
    @Autowired
    private AppConfig appConfig;


    @Bean
    public ThirdService thirdService() {
        return new ThirdServiceImpl(appConfig.transferService());
    }

}

```

@Component 어노테이션이 붙은 클래스는 3가지 방법으로 의존성을 주입할 수 있다. - 생성자, 수정자(setter()), 필드 (@Autowired), 일반 메서드(잘사용 x)

<br>
생성자 주입을 사용하고 옵션이 필요할 때 수정자 주입을 사용한다.

Setter-based Dependency Injection

``` java 
public class SimpleMovieLister {

    // the SimpleMovieLister has a dependency on the MovieFinder
    private MovieFinder movieFinder;

    // a setter method so that the Spring container can inject a MovieFinder
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // business logic that actually uses the injected MovieFinder is omitted...
}
```


<br><br><br>




<br><br><br>
<br><br><br>

<br>

## 스프링 MVC 
---

ResponseEntity

JSON 형태로 데이터를 주고 받을 때 서버가 제공하는 api에는 단순히 값만 전달되지 않는다.
HTTP status code, Header 정보, 등이 존재.
ResponseEntity를 통해 이러한 정보들을 한번에 담아서 전달 가능하다.

<br><br><br>
<br><br><br>
<br><br><br>
<br><br><br>
<br><br><br>
<br><br><br>


++
[shedlock] <br>
how to synchronize ... (stackoverflosw) - https://stackoverflow.com/questions/69988304/spring-synchronize-saving-to-database-with-another-instances <br>
블로그 (db조회데이터 첨부) - https://hea1peak.tistory.com/257 <br>
bealdung - https://www.baeldung.com/shedlock-spring <br>

in maven
difference between artifactid and name - https://stackoverflow.com/questions/69988304/spring-synchronize-saving-to-database-with-another-instances <br>

> artifactid : 프로젝트를 구분하는 식별자, name : 프로젝트의 이름 이라고 구분하면 될 것 같음.

### [참고] <br>

  * **환경설정** <br>
  *-* [*-context.xml] 파일 없이 Bean을 등록하여 사용하는 방법 **@@@@@** - https://stackoverflow.com/questions/8075790/how-to-register-spring-configuration-annotated-class-instead-of-applicationcont?rq=1 <br>

  *-* ServletContextListener 에서 스프링 빈 사용하기 - https://stackoverflow.com/questions/39787519/how-use-autowired-instance-variable-use-in-servletcontextlistener <br>


  * 기초 개념 <br>
  *-* Bean 메서드를 통한 의존성 주입 (inter-bean references) [important] - https://spring.training/understanding-inter-bean-method-reference-in-spring-configuration/ <br>
  
  <br>

  * Listener & Filter 클래스
  *-* How To Call Method after DispatcherServlet Initialization completed - https://stackoverflow.com/questions/45004461/how-to-call-method-after-dispatcherservlet-initialization-completed <br>

  * Spring MVC <br>
  *-* 파일 업로드 방법 설명 - https://caileb.tistory.com/152 <br>
  *-* 파일업로드 방법 예시 1 - https://passionha.tistory.com/214 <br>
  *-* 파일업로드 방법 예시 2 - https://advenoh.tistory.com/26 <br>

  <br>
  
  * Application Deployment <br>
  *-* Springboot deployment [official] - https://docs.spring.io/spring-boot/docs/current/reference/html/deployment.html#deployment.installing.nix-services <br>
