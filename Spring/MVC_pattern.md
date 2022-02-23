# MVC pattern

## web.xml 이해하기 (understand configuration metadata)



<br><br>

## Listener, Filter
서블릿 컨테이너가 web.xml을 읽어들일 때 위에서부터 읽기 때문에 listener와 filter가 여러개 표기되어 있을 때 위에서 아래의 순서로 등록되고 실행된다.



<br><br>

## Servlet 활용
> HttpServletRequest, HttpServletResponse, ... etc.

<br>

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

  * **Servlet**
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

  