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
..