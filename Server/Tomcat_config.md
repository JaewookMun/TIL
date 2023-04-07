# Tomcat Configuration

## **server.xml** structure




<br><br><br>
<br><br><br>

## Tomcat URL Rewrite

HTTP 통신에서 특정 URL에 대한 request 요청을 redirect 할 수 있는 것처럼 서버자체에서 잘못된 URL 및 원하는 URL을 다른 URL로 rewrite할 수 있다.

설정방법 - I. 톰캣 서버 설정 II. 배포 소스파일 설정

I. 톰캣 서버 설정
1. tomcat/conf/server.xml의 <Host> 하위 태그에 RewriteValve 추가
2. tomcat/conf/Catalina/localhost에 (host configuration 폴더) 설정파일 (rewrite.config) 추가
3. [rewrite.config] 설정
4. Tomcat 재시작







<br><br><br>
<br><br><br>

## URL 허용 문자

URL 비허용 문자 : HTTP/1.1 spec 기준으로 url 경로에는 인코딩된 문자가 와야한다. 하지만  " < > [ \ ] ^ ` { | } 문자가 올 경우 인코딩이 안되기 때문에 해당 경로로 접근할 수 없다.

톰캣 server.xml 셋팅 옵션 : relaxedPathChars, relaxedQueryChars



<br><br><br>
<br><br><br>

## Application Deployment

Tomcat startup시 appBase(일반적으로 webapps)에 위치한 application이 자동으로 배포된다.








<br><br><br>
<br><br><br>


### [참고] <br>
  * Tomcat structure description <br>
  *-*  https://www3.ntu.edu.sg/home/ehchua/programming/howto/Tomcat_More.html <br>


  * ~/conf/ - configuration <br>
  *-* Tomcat directory structure & Configuration files - https://tomcat.apache.org/tomcat-3.2-doc/uguide/tomcat_ug.html <br>
  *-* **server.xml** structure explain - https://examples.javacodegeeks.com/enterprise-java/tomcat/tomcat-server-xml-configuration-example/ <br>
  *-* **server.xml** structure with picture - https://howtodoinjava.com/tomcat/tomcats-architecture-and-server-xml-configuration-tutorial/ <br>

  *-* Apache offiction document on [The rewrite Valve] - https://tomcat.apache.org/tomcat-8.0-doc/rewrite.html#mapfunc <br>
  *-* url rewrite 설정방법 (블로그) - https://datajoy.tistory.com/116 <br>

  *-* URI path/query string 특수문자 허용 옵션 [relaxedPathChars 또는 relaxedQueryChars] 검색 - https://tomcat.apache.org/tomcat-8.5-doc/config/http.html <br>

  <br>

  * web app deployment <br>
  *-* Tomcat Web Application Deployment - https://tomcat.apache.org/tomcat-8.5-doc/deployer-howto.html <br>
  

   