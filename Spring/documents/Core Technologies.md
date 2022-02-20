# Core Technologies

스프링 프레임워크 기술들 중에서 가장 중요한 것은 IoC(Inversion of Control) Container 이다.
철저한(강력한) 제어 역전 컨테이너는 포괄적인 범위의 AOP 기술로 이어진다.


**1. The IoC Container**

**1.1 Introduction to the Spring IoC Container and Beans**
IoC는 dependency injection(DI) 로도 알려져있으며 생성자, 팩토리 메서드, 필드(properties)를 통해 의존성 주입이 가능하다. (의존성 주입은 객체가 자신의 의존성을 정의하는 프로세스이다.)

컨테이너는 빈을 생성하며 의존성을 주입 (cf. Service Locator Pattern)

BeanFactory, ApplicationContext (ApplicationContext가 Web Application에 더 적합 - Application Layer)


<br><br>

**1.2. Container Overview**
org.springframework.context.ApplicationContext 인터페이스는 Spring IoC container를 의미하며 스프링빈 객체를 관리하는 역할을 한다. container는 configuration metadata를 읽어서 빈 관리 정보(생성할 객체와 객체들간의 의존관계)를 얻으며 메타데이터는 XML, Java annotation, 또는 Java code로 제공된다.

![container-magic.png](../images/container-magic.png)
Spring IoC container

ApplicationContext가 생성되고 초기화 되면 실행가능한 어플리케이션의 설정이 완료된다.


<br><br>

**1.2.1. Configuration Metadata**
Spring container가 읽어들이는 설정 메타정보는 어플리케이션에서 객체의 생성, 설정, 조립을 어떻게 하는지에 대한 정보를 담고 있다.

설정 메타정보는 XML 형태로 제공되어왔으나 최근의 많은 개발자들은 자바 코드 형태의 메타정보 설정방식을 사용한다.
> 위 해석은 다소 부적합

* XML-based configuration
* Annotation-based configuration
* Java-based configuration

Spring configuration은 1개 이상의 빈 설정으로 구성된다. XML 방식은 <bean/>엘리먼트를 <beans/>엘리먼트 내부에 설정하고 Java 방식은 @Configuration 클래스내부에 @bean 어노테이션이 사용된 메소드를 통해 설정한다.


**1.2.2. Instantiating a Container**
..

