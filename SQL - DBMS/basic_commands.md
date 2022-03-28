# Commands

## MySQL

### DML (Data Manipulation Language)

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

<br>

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
<br><br>
<br><br>

### [참고]
  *-* 기본 SQL 문장이란 (mariadb doc) - https://mariadb.com/kb/ko/basic-sql-statements/ <br>

  * **DML**
  *-* mariaDB > Returning [Document] - https://mariadb.com/kb/en/insertreturning/ <br>
  *-* insert후 값 가져오기(블로그) - https://hochoon-dev.tistory.com/entry/SpringBoot-Mybatis-Insert-%ED%95%9C-%EA%B0%92%EC%9D%98-AUTOINCREMENT%EB%90%9C-ID-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0 <br>

  *-* 데이터 일괄변경 [REPLACE] - https://yeop-blog.github.io/2017/10/02/2017-10-02-old-blog-post88/ <br>
  
  *-* https://linuxism.ustd.ip.or.kr/510 <br>

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