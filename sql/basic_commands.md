## Commands

### MySQL

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

* [참고]
  *-* 데이터베이스 - https://jjeongil.tistory.com/1322 <br>
  *-* 계정변경 - https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=athena1028&logNo=20060725715 <br>
  *-* 유저 권한 설정 - https://fun25.co.kr/blog/mysql-grant-user-privileges/?page=9 <br>
  *-* https://linuxism.ustd.ip.or.kr/510 <br>