# 스프링 (Spring)

<br>

## 스프링 설정
---

<br>

### Spring Legacy

### SpringBoot


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

추가로 @Configuration 클래스 내부에 선언된 다른 메서드를 내부에서 호출하여 의존성을 주입할 수도 있다.

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



<br><br>

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



### [참고] <br>
  * **환경설정**
  *-* [*-context.xml] 파일 없이 Bean을 등록하여 사용하는 방법 **@@@@@** - https://stackoverflow.com/questions/8075790/how-to-register-spring-configuration-annotated-class-instead-of-applicationcont?rq=1 <br>

  <br>

  * Spring MVC
  *-* 파일 업로드 방법 설명 - https://caileb.tistory.com/152 <br>
  *-* 파일업로드 방법 예시 1 - https://passionha.tistory.com/214 <br>
  *-* 파일업로드 방법 예시 2 - https://advenoh.tistory.com/26 <br>

  