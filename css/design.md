# 문서 디자인


### 구조
---


* 레이아웃

  - z-index : position 속성과 연관이 있기 때문에 position: static 이면 우선순위를 설정할 수 없다. 





### 테이블

* 반응형 테이블 스크롤 자동생성

``` css
@media (max-width: 575.98px) {}  /* 미디어 쿼리 max width 설정 */

.table-container {
  width: 100%;
  overflow-x: auto;
  white-space: nowrap; /* 해당 속성을 nowrap으로 설정안하면 글자가 세로로 표시. */
}

.table {
  width: auto;
}

```


### 글자 

css 속성값 user-select를 none으로 설정하여 사용자의 글자 드래그를 방지할 수 있다.

``` css
.example {
  user-select: none;  /* 글씨 드래그 방지 */
}


```


<br>




### [참고] <br>
  
  *-* z-index - https://abcdqbbq.tistory.com/39 <br>
  *-* 테이블 스크롤(종,횡) 자동생성 방법 - https://dailyscript.tistory.com/entry/%EB%B0%98%EC%9D%91%ED%98%95-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EA%B0%80%EB%A1%9C-%EC%8A%A4%ED%81%AC%EB%A1%A4-%ED%9A%A1%EC%8A%A4%ED%81%AC%EB%A1%A4-%EC%A0%81%EC%9A%A9-%EB%B0%A9%EB%B2%95 <br>
  *-* 글자(폰트) 그림자 - https://mintaku.tistory.com/27 <br>

