# MVC pattern

## web.xml 이해하기 (understand configuration metadata)



<br><br>

## Listener, Filter
서블릿 컨테이너가 web.xml을 읽어들일 때 위에서부터 읽기 때문에 listener와 filter가 여러개 표기되어 있을 때 위에서 아래의 순서로 등록되고 실행된다.





<br><br>

@EnableWebMvc

Spring 프레임워크에서 필요한 초기값을 세팅해줌.


<br><br>
<br><br>

## Servlet 활용
> HttpServletRequest, HttpServletResponse, ... etc.

<br>

RequestContextHolder 사용법
``` java
  public void report() throws ServletException, IOException {
    final ServletRequestAttributes currentRequestAttributes = (ServletRequestAttributes) RequestContextHolder
        .currentRequestAttributes();
    final HttpServletRequest httpServletRequest = currentRequestAttributes.getRequest();
    final HttpServletResponse httpResponse = currentRequestAttributes.getResponse();

    reportServlet.service(httpServletRequest, httpResponse);

```

## 영속성 유지 방법 (Connection 관리)

<br>

### **Cookie**

서버 클라이언트간 영속성을 유지하기 위해 저장 매체로 세션과 쿠키가 사용되며
주로 클라이언트 단에 데이터를 전달하기 위해 사용된다.

<br>

**Cookie의 path 속성과 전송 규칙**
path 속성을 통해 웹서버의 특정 URL에 대해서 쿠키를 전달할 수 있다. path 속성은 웹서버의 디렉토리 형태로 지정 가능하며
경로를 지정하면 해당 URL과 하위 경로에만 쿠키가 전송된다. (디렉토리 단위는 /로 구분되어지는 단위를 의미)

c.f.) domain 속성 & '/' <br>
c.f.) path를 '/path/'로 지정하면 '/path/~'의 url에서만 쿠키를 확인할 수 있다. '/otherpath/'에서는 불가능





<br><br>


<br><br>

**페이지 이동 - 2가지 방법**
* httpServletRequest.**getRequestDispatcher**(path).**forword**(request, response) :
* httpServletResponse.**sendRedirect**(path) : 



<br>

Redirect 활용
1. request.setAttribute 활용
2. FlashMap 활용 

<br>


## Controller

* 데이터 받기

* 데이터 전송

<br>

## ResponseEntity  
*-* 단순히 ResponseBody 정보를 전달하는 것을 넘어서 헤더정보와 HTTP 상태코드를 함께 전달 가능


<br><br>


### [참고] <br>
  * configuration metadata
  *-* listener [web.xml] - https://dev-room.tistory.com/84 <br>
  *-* 여러개의 filter 등록 및 순서 지정 - https://dololak.tistory.com/599 <br>

  *-* @EnableWebMvc는 어떤 역할을 하는가?  - https://goodgid.github.io/Spring-Enable-MVC-Annotation/ <br>

  * **Servlet**
  *-* RequestContextHolder > getResponse() - https://www.tabnine.com/code/java/methods/org.springframework.web.context.request.ServletRequestAttributes/getResponse <br>

  * **영속성 유지**
  *-* 쿠키 path 속성 - https://dololak.tistory.com/546 <br>

  *-* 리다이렉트 방법 차이점 from request, response -  https://stackoverflow.com/questions/7220241/whats-the-difference-between-requestdispatcher-forward-and-httpservletrespons <br>
  *-* 리다이렉트 FlashMapManager 참고 - https://stackoverflow.com/questions/23844546/flash-attribute-in-custom-authenticationfailurehandler/50429613 <br>
  *-* RedirectAttributes 예시 - https://velog.io/@godkimchichi/Spring-37.2-Spring-Security <br>

  *-* Controller와 Service에 작성하는 로직의 구분 근거 - https://okky.kr/article/367591?note=1161511 <br>
  *-* 서비스에 비즈니스 로직을 작성하는 이유 - https://okky.kr/article/367591?note=1161511 <br>
  *-* ajax 통신으로 js 배열 받는 방법 - https://go-coding.tistory.com/60 <br>
  
  * **REST api**
  *-* Rest Api with Spring MVC (SOAP vs REST) - https://rebeccacho.gitbooks.io/spring-study-group/content/chapter16.html <br>
  *-* SOAP 란? wiki - https://ko.wikipedia.org/wiki/SOAP <br>
  *-* map 객체 전달방법 (Q: ResponseEntity란?) - https://stackoverflow.com/questions/31239481/how-to-use-responsebody-to-return-a-mapstring-string <br>
  *-* ResponseEntity 란? - https://hyeonic.tistory.com/197 <br>
  *-* ResponseEntity 사용 예시 1 - https://devlog-wjdrbs96.tistory.com/197?category=882974 <br>
  *-* ResponseEntity 사용 예시 2 (위의 예시를 좀 더 간단히 표기) - https://devlog-wjdrbs96.tistory.com/182 <br>

  