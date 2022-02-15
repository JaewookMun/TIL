# Java API


<br>

## List, Map

#### Map

* keySet(), entrySet() 등 안 사용해본 메소드 공부 필요..

<br>

## 함수형 인터페이스 (Functional Interface)



## 스트림(Stream)

<br>

## Optional

Optional 활용을 위한 기본 기능 

[static method] - 생성, return Optional<T>

* Optional.of(T value)
* Optional.ofNullable(T value)
* Optional.empty()

<br>

[instance method] - method chaining, return value
* filter()
* map()
---
* isPresent()
* ifPresent(Consumer<? super T> consumer)
* get()
* orElse(T other)
* orElseGet(Supplier<? extends T> other)
* orElseThrow(Supplier<? extends X> exceptionSupplier)

> filter(), map() 메소드 익숙해지기...

<br>




> cf.) Optional<T>에서 제네릭 T는 Type의 약자이다.
<br>

<br>



### [참고] <br>
  *-* static 사용을 피해야하는 이유 - https://kellis.tistory.com/127 <br>

  * **Stream**
  *-* 기본적인 스트림 사용법 - https://coding-factory.tistory.com/574 <br>
  *-* 레거시 vs modern 고찰 - http://homoefficio.github.io/2016/06/26/for-loop-%EB%A5%BC-Stream-forEach-%EB%A1%9C-%EB%B0%94%EA%BE%B8%EC%A7%80-%EB%A7%90%EC%95%84%EC%95%BC-%ED%95%A0-3%EA%B0%80%EC%A7%80-%EC%9D%B4%EC%9C%A0/ <br>
  

  * **Optional**
  *-* Java official api doc - https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html <br>
  *-* optional to string - https://codechacha.com/ko/java8-stream-optional/ <br>
  *-* Optional 사용법 1(블로그) - https://hbase.tistory.com/212 <br>
  *-* Optional 사용법 2(블로그) - https://tecoble.techcourse.co.kr/post/2021-06-20-optional-vs-null/ <br>
  
