# Commands

## MySQL

### DQL

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

<br>

### ?

Database 및 사용자 설정
* Database 생성
* 사용자 조회
* 사용자 추가 / 생성
* 사용자 삭제
* 


<br><br>

### [참고]
  * DQL
  *-* mariaDB > Returning [Document] - https://mariadb.com/kb/en/insertreturning/ <br>
  *-* insert후 값 가져오기(블로그) - https://hochoon-dev.tistory.com/entry/SpringBoot-Mybatis-Insert-%ED%95%9C-%EA%B0%92%EC%9D%98-AUTOINCREMENT%EB%90%9C-ID-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0 <br>

  *-* 데이터베이스 - https://jjeongil.tistory.com/1322 <br>
  *-* 계정변경 - https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=athena1028&logNo=20060725715 <br>
  *-* 유저 권한 설정 - https://fun25.co.kr/blog/mysql-grant-user-privileges/?page=9 <br>
  *-* https://linuxism.ustd.ip.or.kr/510 <br>

  * database, user CRUD
  *-* DB 생성 - https://devdhjo.github.io/mysql/2020/01/29/database-mysql-002.html <br>
  *-* DB 사용자 추가방식 (create / grant) - https://technote.kr/32 <br>
  *-* DB 사용자 권한 설정 - https://damduc.tistory.com/4 <br>