# MySQL Commands

## Transaction

데이터베이스에서 발생하는 논리적 작업단위. 데이터베이스에서는 데이터의 무결성을 지키기 위해 ACID라는 4가지 속성을 가진다.
(Atomic, Consistency, Isolation, Durability)


<br><br>


Autocommit 연관 commands

``` sql
-- autocommit 설정정보 확인
SELECT @@AUTOCOMMIT;

-- autocommit 설정/해제
set autocommit = true;
set autocommit = false;

commit;
rollback;

```

<br><br><br>

## (Transaction) Isolation Level (격리/고립 수준)

트랜젝션 간 데이터 처리를 얼마나 허용할 것인지 정해놓은 수준
> 격리수준이 높을 수록 데이터일관성은 높아지지만 성능은 하락한다.

[격리수준]
* Read Uncommited (level 0)
* Read Commited (level 1)
* Repeatable Read (level 2)
* Serializable (level 3)



<br><br><br>

_*_ 데이터베이스 엔진(스토리지 엔진)에 따라 트랜젝션의 지원 유무가 다르다. - MariaDB에서는 storage engine으로 표기


MariaDB의 기본 DB엔진은 InnoDB이다. (MariaDB 10.2 버전 이후로 적용, 이전버전은 XtraDB를 기본 DB엔진으로 사용)
(InnoDB는 XtraDB와 유사한 기능을 제공하며 version 변경으로 인한 migration 시 시간적으로 효율적이기 때문에 InnoDB를 default로 제공)

<br>



아래 명령어를 통해 설정가능한 데이터베이스 엔진을 확인할 수 있다.
> show engines;












<br><br><br>
<br><br><br>

## DML (Data Manipulation Language)
---
SELECT의 경우 DQL(데이터 질의어)라고도 불린다.


데이터 조작어에는 **SELECT**, **INSERT**, **UPDATE**, **DELETE** 등이 있다.


* INSERT INTO `테이블`(...) VALUES(...) **RETURNING** id[, name ...]
  > returning을 통해 insert한 컬럼값들을 가져올 수 있음.


* Access
  ``` sql
  mysql -u 계정 -p [데이터베이스]
  ```
  
* 데이터베이스 조회 / 선택 명령어
  show databases;
  use database_name;

* 계정 추가(권한설정과 함께 추가?)
``` sql
mysql> grant all privileges on dbname.table to userid@host identified by 'password';
```


* 날짜 출력 : DATE() 사용.

* 기존 데이터 일괄 변경 : REPLACE()



<br><br><br>

### 중복데이터 조회 해결

SELECT 조회 시 데이터의 중복문제는 DISTINCT 키워드 or GROUP BY 절을 통해 해결가능


주의
* distinct의 경우 비교되는 행들 사이의 모든 컬럼값이 같지 않으면 별개의 행으로 처리
* group by를 사용해 중복을 제거하려는 컬럼값을 기준으로 데이터를 읽을 수 있다.
* group by시 생략되는 행의 다른 컬럼값을 사용하기 위해서 max() 등의 함수를 활용




<br><br><br>
<br><br><br>
<br><br><br>


### DDL (Data Definition Language)

데이터 정의어에는 **CREATE**, **ALTER**, **DROP**  등이 있다.

<br><br>

#### Database 및 사용자 관리
* Database 생성
* 사용자 조회
* 사용자 추가 / 생성
* 사용자 삭제
* 

<br>

사용자 계정 생성 및 권한 부여
---

<br>

사용자 생성 <br>
: CREATE USER 'username'@'host' IDENTIFIED BY 'password'

``` sql
  > CREATE USER mun1103@'localhost' IDENTIFIED BY 'a1234'; -- 로컬

  > CREATE USER globaljw@'%' IDENTIFIED BY 'a1234';   -- 외부에서 접속가능

```

<br>

사용자 삭제 <br>
: DROP USER 'username'@'host'

<br><br>



권한 부여 <br>
: GRANT ALL PRIVILEGES ON 'database_name'.'table' TO 'username'@'host' [IDENTIFIED BY 'password']

* DB스키마.table에서 와일드카드 \*는 모든 것을 의미한다. 예를 들어 A.\* 는 A 데이터베이스의 모든 테이블에 대한 권한을 부여할 때 사용한다.

<br>

``` SQL
  GRANT ALL PRIVILEGES ON lottery.* TO jack@localhost;

```

<br>

권한 삭제 <br>
: REVOKE ALL ON 'database_name'.'table' FROM 'username'@'host'



<br>

새로고침 <br>
: FLUSH PRIVILEGES;  // 권한 부여 후 새로고침을 해주어야함.




<br>

계정 조회 <br>
: SELECT user, host FROM USER;

``` sql
  > mysql -u root -p
  
  > use mysql;  -- 데이터베이스 mysql 사용
  > select user, host from user;

  > show databases; -- 데이터베이스 목록 조회
  > show tables;  -- 테이블 목록 조회

```



<br>




<br><br>
<br><br>
<br><br>



제약조건 관리
---

제약조건 확인 <br>
: select * from information_schema.table_constraints;


<br>

제약조건 삭제 <br>
: ALTER TABLE [테이블명] DROP CONSTRAINT [제약조건이름];

: ALTER TABLE [테이블명] DROP FOREIGN KEY [제약조건이름];





<br><br>

## 도움

현재 실행중인 쿼리 확인 및 특정 프로세스 종료 명령어
sql> show processlist;
sql> kill id



<br><br><br>

<br><br><br>

### [참고]
  *-* 기본 SQL 문장이란 (mariadb doc) - https://mariadb.com/kb/ko/basic-sql-statements/ <br>
  <br>

  * DB엔진, Transaction <br>
  *-* Transaction의 Isolation Level 이란? - https://skytitan.tistory.com/265 <br>
  *-* Transaction의 Isolation Level 이란? [better] - https://it-license.tistory.com/25 <br>
  *-* isolation level 및 locking 전략 [@@@@@] - https://suhwan.dev/2019/06/09/transaction-isolation-level-and-lock/ <br>

  *-* 데이터베이스 엔진이란? - https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EC%97%94%EC%A7%84 <br>
  *-* InnoDB, XtraDB, MyISAM 비교 [@@@@@] - https://idchowto.com/myisam-innodb-xtradb-%ED%8A%B9%EC%A7%95-%EB%B0%8F-%EC%84%A4%EC%A0%95/ <br>
  *-* MySQL의 DB엔진 종류 및 특징 - https://nomadlee.com/mysql-%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%EC%97%94%EC%A7%84-%EC%A2%85%EB%A5%98-%EB%B0%8F-%ED%8A%B9%EC%A7%95/ <br>

  <br>


  * **DML**
  *-* mariaDB > Returning [Document] - https://mariadb.com/kb/en/insertreturning/ <br>
  *-* insert후 값 가져오기(블로그) - https://hochoon-dev.tistory.com/entry/SpringBoot-Mybatis-Insert-%ED%95%9C-%EA%B0%92%EC%9D%98-AUTOINCREMENT%EB%90%9C-ID-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0 <br>

  *-* 데이터 일괄변경 [REPLACE] - https://yeop-blog.github.io/2017/10/02/2017-10-02-old-blog-post88/ <br>
  
  *-* https://linuxism.ustd.ip.or.kr/510 <br>

  *-* 데이터 중복 제거 (Okky 질의) - https://okky.kr/article/511810 <br>
  *-* 데이터 중복 제거 group by & max() - http://b1ix.net/87 <br>


  * **DDL**
  *-* DB 생성 - https://devdhjo.github.io/mysql/2020/01/29/database-mysql-002.html <br>
  *-* 데이터베이스 - https://jjeongil.tistory.com/1322 <br>
  *-* 계정변경 - https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=athena1028&logNo=20060725715 <br>
  *-* 유저 권한 설정 - https://fun25.co.kr/blog/mysql-grant-user-privileges/?page=9 <br>
  *-* DB 사용자 추가방식 (create / grant) - https://technote.kr/32 <br>
  *-* DB 사용자 권한 설정 - https://damduc.tistory.com/4 <br>

  *-* 테이블 제약조건 확인 쿼리 - https://dataedo.com/kb/query/mysql/check-column-nullable <br>

  *-* 테이블 CRUD - https://mcpaint.tistory.com/194 <br>
  *-* 테이블 컬럼 null 가능하게 변경 - https://sql-factory.tistory.com/1003 <br>
  *-* 제약조건 확인 및 관리 - https://blog.naver.com/PostView.nhn?blogId=imf4&logNo=220779978513&categoryNo=26&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView <br>

  *-* 현재 실행중인 쿼리 확인 - https://ssssssu12.tistory.com/10 <br>