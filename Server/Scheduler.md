# Scheduler


## 서버 인스턴스

클라우드 서비스를 사용자에게 제공할 때 서버 인스턴스를 한개 or 2개 이상을 제공한다.

인스턴스당 하나의 DB를 가질 수 도 있지만 리소스 측면에서 손해일 수 있음.


<br><br><br>

## 멀티 테넌시 아키텍쳐 (Multi-Tenancy Architecture)

단일 어플리케이션(소프트웨어 인스턴스)으로 서로 다른 여러 사용자 그룹에 서비스를 제공할 수 있는 소프트웨어 구조

![multi-tenancy](./img/multi-tenancy.jpg)

<br>


멀티 테넌시 구현 방식
1. Separate-databases: Each tenant has its own database
2. Separate schemas: Tenants share common database but each tenant has its own set of tables (schema)
3. Shared schema: Tenants share common schema and are distinguished by a tenant discriminator column

cf. MySql에서 스키마(schema)는 database와 동일한 의미를 갖는다. 



### [참고]
  * Multi Tenancy Architecture <br>
  *-* 멀티테넌시란? - https://www.redhat.com/ko/topics/cloud-computing/what-is-multitenancy <br>
  *-* Multi-Tenancy using JPA [Architecture] - https://www.ricston.com/blog/multitenancy-jpa-spring-hibernate-part-1/ <br>
  *-* schema and database in mysql - https://seoulitelab.tistory.com/entry/MySql-schema%EC%8A%A4%ED%82%A4%EB%A7%88%EC%99%80-database%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90 <br>


  *-* how to set one scheduler for multiple instance [check] - https://stackoverflow.com/questions/62994659/running-only-once-a-schedule-job-across-multiple-instances <br>
  *-* spring batch with multi tenancy - https://stackoverflow.com/questions/25516951/spring-batch-with-multi-tenancy <br>

