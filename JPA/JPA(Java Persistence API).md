# JPA (Java Persistence Api)

## 데이터베이스 연결

**SQL Mapper** 
* ex) Mybatis, JdbcTemplate
* 관계형 데이터베이스의 구조에 종속적인 코드를 작성




<br><br><br>

**ORM (Object Relational Mapping) : 객체 관계 매핑**
* ex) JPA(<- Hibernate)
* 객체지향적인 프로그래밍 방식을 활용하여 코드를 작성

> JPA에서 가장 중요한 개념
> 1. 객체와 관계형 데이터베이스 연결(Mapping)
> 2. 영속성 컨텍스트

* 영속성 컨텍스트는 엔티티 매니저(EntityManager)를 통해 접근할 수 있고 EntityManager는 엔티티의 영속성을 관리한다.

<br><br><br>
<br><br><br>


## 영속성 컨텍스트




## 객체 매핑





<br><br><br>
<br><br><br>
<br><br><br>

### [참고]
  *-* ORM 과 SQL Mapper 의 차이점 - https://velog.io/@adam2/JPA%EB%8A%94-%EB%8F%84%EB%8D%B0%EC%B2%B4-%EB%AD%98%EA%B9%8C-orm-%EC%98%81%EC%86%8D%EC%84%B1-hibernate-spring-data-jpa <br>
  *-* JPA, MyBatis 동시사용 - https://jforj.tistory.com/91 <br>
  *-* https://goodteacher.tistory.com/344 <br>

  *-* JPA association(연관관계) CASCADE TYPE 설명(블로그) - https://data-make.tistory.com/668 <br>
  *-* JPA association(연관관계) CASCADE TYPE original source - https://www.baeldung.com/jpa-cascade-types <br>