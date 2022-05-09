# Rendering

렌더링이란?
> 화면에 표시할 웹 페이지를 만드는 과정

렌더링 과정
1. HTML 파일과 CSS 파일을 파싱하여 각각 Tree를 생성 (Parsing)
2. 두 Tree를 결합하여 Rendering Tree 생성 (Style)
3. Rendering Tree에서 각 노드의 위치와 크기를 계산 (Layout)
4. 계산된 값을 이용해 각 노드를 화면상의 실제 픽셀로 변환하고, 레이어를 생성(Paint)
5. 레이어를 합성하여 실제 화면에 출력 (Composite)

### [참고] <br>
  *-* 렌더링이란? - https://defineall.tistory.com/707 <br>
  *-* 브라우저의 동작원리 - https://d2.naver.com/helloworld/59361 <br>
  *-* 렌더링 과정 - https://tecoble.techcourse.co.kr/post/2021-10-24-browser-rendering/ <br>