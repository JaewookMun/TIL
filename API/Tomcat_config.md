# Tomcat Configuration

## Tomcat URL Rewrite

HTTP 통신에서 특정 URL에 대한 request 요청을 redirect 할 수 있는 것처럼 서버자체에서 잘못된 URL 및 원하는 URL을 다른 URL로 rewrite할 수 있다.

설정방법 - I. 톰캣 서버 설정 II. 배포 소스파일 설정

I. 톰캣 서버 설정
1. tomcat/conf/server.xml의 <Host> 하위 태그에 RewriteValve 추가
2. tomcat/conf/Catalina/localhost에 (host configuration 폴더) 설정파일 (rewrite.config) 추가
3. [rewrite.config] 설정
4. Tomcat 재시작

### [참고] <br>
  *-* Apache offiction document [The rewrite Valve] - https://tomcat.apache.org/tomcat-8.0-doc/rewrite.html#mapfunc <br>
  *-* url rewrite 설정방법 (블로그) - https://datajoy.tistory.com/116 <br>

   