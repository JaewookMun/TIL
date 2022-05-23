# Java API

## Java CLI



> javac HelloWorld.java
> java java HelloWorld


<br><br><br>

## static keyword (static vs instance)

정적 메서드는 언제 사용해야하는가?

> One rule-of-thumb: ask yourself "Does it make sense to call this method, even if no object has been constructed yet?"
>  If so, it should definitely be static.

객체 생성 없이 메서드를 호출하는 상황이 논리적으로 타당하면 static 메서드를 사용해도 좋다.

<br>

정적메서드의 2가지 특징
1. 클래스의 인스턴스 생성 없이 호출할 수 있는 메서드 (인스턴스에서는 호출할 수 없다.)
2. 유틸리티 함수를 만드는데 유용하게 사용된다. eg) Math 클래스


<br><br>

Static 사용을 피해야하는 이유는? - refer to below links



<br><br><br>
<br><br><br>

## Enum

열거형 - 상수를 모아서 처리할 수 있음.

<br><br>


<br>

## List, Map
---

### **Map**

* keySet(), entrySet() 등 안 사용해본 메소드 공부 필요..


<br><br><br>

## 함수형 인터페이스 (Functional Interface)
---


### **스트림(Stream)**

스트림의 특징
* 자료의 대상과 관계없이 동일한 연산을 수행
* 한번 생성하고 사용한 스트림은 재사용 불가
* 스트림의 연산은 기존 자료를 변경하지 않음
* 스트림의 연산은 중간 연산과 최종 연산이 존재
  - 중간 연산은 여러 개 적용될 수 있고 최종 연산은 단 한번만 적용
  - 중간 연산이 여러 개 호출 되었더라도 최종 연산이 호출되어야 스트림의 모든 중간 연산이 적용
    -> 최종 연산이 호출되지 않으면 정렬 및 검색결과를 가져올 수 없고 이는 지연 연산(lazy evaluation)이라 불림



<br><br>

### **Optional**

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


<br><br><br>

## Inner Class

static inner class

Q: inner class에 static을 붙이는 이유는?
inner 클래스에 static의 유무가 주는 가장 큰 차이는 외부에서의 접근성이다.

static이 없으면 inner 클래스는 outer 클래스의 인스턴스를 통해서만 접근가능하지만, static이 있다면 독립적으로 생성되기 때문에 외부에서 쉽게 접근할 수 있다.





<br><br><br>


<br><br><br>

## File I/O
---

### File

위치정보를 가지고 인스턴스를 만들어서 필요한 디렉토리 및 파일을 생성할 수 있다.
File 등 자바에서 기본으로 제공하는 API를 통해 파일의 기본적인 속성 및 여러가지 정보를 조회할 수 있다. 하지만 파일의 버전 정보 등 일부 자세한 정보를 조회하기 위해서는 JNA(Java Native Access) 라이브러리를 사용해야한다.

<br><br>

파일 옮기기

사용 클래스 및 인터페이스 : File, FileInputStream, MultipartFile, MockMultipartFile (Spring)

``` java
multipartFile.transferTo(String path); // 디렉토리 경로일 경우 에러(FileNotFoundException) 발생

new FileInputStream(File file); // 디렉토리의 인스턴스일 경우 에러(FileNotFoundException) 발생

```

<br><br>

FileNotFoudException ~ (액세스가 거부되었습니다.)
> File 인스턴스를 사용시 해당 문구의 Exception이 발생하면 1. 관리자 권한으로 실행, 2. File 인스턴스가 실제 파일이 아니라 Directory인지 확인


<br><br><br>

## Network Programming API

### URL

URL 클래스를 사용해서 웹자원을 읽어올 수 있음. - InputStream / OutputStream 활용 참고


URL 객체에 사용하는 url 경로에는 특수문자를 사용할 수 없다.
> url 경로에 공백(스페이스)가 들어가면 에러가 발생한다. <br>
> '[에러]요청 타겟에서 유효하지 않은 문자가 발견되었습니다. 유효한 문자열은 RFC7230과 RFC3986에 정의되어 있습니다.'





<br><br><br>

<br><br><br>



### [참고] <br>
  * Java CLI <br>
  *-* Java execution with CLI (Could Not Find or Load) - https://www.baeldung.com/java-could-not-find-load-main-class <br>
  *-* Java CLI with multiple args - https://lightrun.com/java/java-tutorial-java-command-line-arguments/ <br>

  <br>

  * static field / method <br>
  *-* 정적 메서드는 언제 써야하는가? - https://mygumi.tistory.com/253 <br>
  *-* (위 블로그 참고링크) when to use static method - https://stackoverflow.com/questions/2671496/when-to-use-static-methods <br>
  *-* static 사용을 피해야하는 이유 - https://kellis.tistory.com/127 <br>

  *-* method chaining drawback? - https://softwareengineering.stackexchange.com/questions/80244/are-there-any-actual-drawbacks-to-self-referential-method-chaining <br>

  *-* Enum 우아한 형제 기술 블로그 - https://techblog.woowahan.com/2527/ <br>

  * **Stream** <br>
  *-* 기본적인 스트림 사용법 - https://coding-factory.tistory.com/574 <br>
  *-* 레거시 vs modern 고찰 - http://homoefficio.github.io/2016/06/26/for-loop-%EB%A5%BC-Stream-forEach-%EB%A1%9C-%EB%B0%94%EA%BE%B8%EC%A7%80-%EB%A7%90%EC%95%84%EC%95%BC-%ED%95%A0-3%EA%B0%80%EC%A7%80-%EC%9D%B4%EC%9C%A0/ <br>
  

  * **Optional** <br>
  *-* Java official api doc - https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html <br>
  *-* optional to string - https://codechacha.com/ko/java8-stream-optional/ <br>
  *-* Optional 사용법 1(블로그) - https://hbase.tistory.com/212 <br>
  *-* Optional 사용법 2(블로그) - https://tecoble.techcourse.co.kr/post/2021-06-20-optional-vs-null/ <br>

  * Inner Class <br>  
  *-* inner 클래스에서 static을 붙이는 이유 - https://www.inflearn.com/questions/257297 <br>
  *-* Nested Classes in Java - https://www.baeldung.com/java-nested-classes <br>

  * File IO <br>
  *-* 파일 속성 읽는 방법 [Doc] - https://docs.oracle.com/javase/tutorial/essential/io/fileAttr.html <br>
  *-* 자바로 파일 속성 읽는 방법 [기본속성] - https://okky.kr/article/297810 <br>
  *-* how to read file attribute in java - https://stackoverflow.com/questions/18129120/how-to-read-file-properties-details-content-pages-e-g-for-a-word-documen <br>
  *-* get version of .exe file [JNA] - https://stackoverflow.com/questions/6918022/get-version-info-for-exe <br>
  *-* FileInputStream 예외 [FileNotFoundException] 발생 이유 (디렉토리를 읽으면 발생) - https://stackoverflow.com/questions/13046757/how-to-read-a-folder-count-the-files-and-copy-to-new-folder <br>
  *-* XML Parsing process in java (수정방법) - https://www.w3schools.blog/dom-parser-to-modify-xml-file-in-java <br>

  * InputStream <br>
  *-* InputStream(Reader) to String (read메서드를 사용하면 int를 반환 char로 바꾸어준다.) - https://www.baeldung.com/convert-input-stream-to-string <br>

  * Network Programming <br>
  *-* url encoding 개념설명 블로그 - https://dololak.tistory.com/18 <br>
  *-* Java URL Encoding / Decoding java progamming ex [Baeldung] - https://www.baeldung.com/java-url-encoding-decoding <br>
  *-* URL 클래스 사용 예시 - https://hackeen.tistory.com/18 <br>
