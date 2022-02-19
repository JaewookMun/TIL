# Core Technologies

스프링 프레임워크 기술들 중에서 가장 중요한 것은 IoC(Inversion of Control) Container 이다.
철저한(강력한) 제어 역전 컨테이너는 포괄적인 범위의 AOP 기술로 이어진다.


**1. The IoC Container**

**1.1 Introduction to the Spring IoC Container and Beans**
IoC는 dependency injection(DI) 로도 알려져있으며 생성자, 팩토리 메서드, 필드(properties)를 통해 의존성 주입이 가능하다. (의존성 주입은 객체가 자신의 의존성을 정의하는 프로세스이다.)

컨테이너는 빈을 생성하며 의존성을 주입 (cf. Service Locator Pattern)

BeanFactory, ApplicationContext (ApplicationContext가 Web Application에 더 적합 - Application Layer)

<br>

**1.2. Container Overview**
org.springframework.context.ApplicationContext 인터페이스는 Spring IoC container를 의미하며 스프링빈 객체를 관리하는 역할을 한다. container는 configuration metadata를 읽어서 빈 관리 정보(생성할 객체와 객체들간의 의존관계)를 얻으며 메타데이터는 XML, Java annotation, 또는 Java code로 제공된다.

![container-magic.png](../images/container-magic.png)
Spring IoC container

ApplicationContext가 생성되고 초기화 되면 실행가능한 어플리케이션의 설정이 완료된다.

<br>

**1.2.1. Configuration Meta**
..
