# Mapping (맵핑)

## Parameter

<br>

**1개**의 String parameter를 사용할 경우

dao 인터페이스의 메서드에 String 파라미터가 하나만 있을 때 mapper에서 스트링 값을 대체할 경우 
> There is no getter for property named 'search' in 'class java.lang.String' <br>

위 에러가 발생할 수 있다. 해당 에러는 #{} 문법을 사용할 때 중괄호 안에 value(지정된 표기값)를 표기하면 해결된다.

* DTO 객체 or Map 객체를 만들어서 해결할 수 있으나 1개의 파라미터를 위해 만들기에는 번거로운 점이 존재.


<br><br><br>
<br><br><br>
<br><br><br>


* 2개 이상의 파라미터를 맵핑하는 방법
  - VO, Map, @Param 사용


* 다른 .xml 파일에 있는 resultMap 을 재사용할 수 있다.
  -> namespace.id 형태로 다른 mapper 파일의 resultMap을 참조


### #{}, ${} 표기법의 차이
**문자열 대체** (String Substitution)
#{} 문법을 사용하면 전달하는 값 양옆에 작은 따옴표('', Single Quotation)이 붙는다.
때문에 변하지 않는 값으로 삽입이 필요한 구문 (ex. ORDER BY )에서는 쿼리가 제대로 실행되지 않기 때문에 값을 그대로 넣는 ${} 문법을 사용

${} 표기법을 사용하여 직접 넣으면 보안상 안전하지 않음.


<br><br>  

## Results


<br><br>

## 동적 SQL

### **foreach**
collection에 대해 반복처리 <br>
foreach엘리먼트의 item 속성, index 속성 참고.
<br>

``` sql
  -- list<일반객체>  e.g.) List<Supplier>
  ~
    <foreach collection="list" item="supplier" separator=",">
      (#{supplier.name})
    </foreach>
  ~

  -- list<Wrapper클래스>  e.g.) List<Integer>
  ~
    IN (
    <foreach collection="list" item="item" index="index" separator=",">
      #{item}
    </foreach>
    )
  ~

  -- Map<>  -> index 속성이 key가 되고 #{item.value} 의 value가 key에 대응하는 값이 됨.

```


### [참고] <br>
  * Official Doc
  *-* MyBatis 공식 페이지 - https://mybatis.org/mybatis-3/ko/sqlmap-xml.html#insert_update_and_delete <br>
  *-* 문자열 대체 (String Substitution) #{value}, ${value} - https://mybatis.org/mybatis-3/ko/sqlmap-xml.html <br>

  * others
  *-* mybatis #{}, ${} 차이점(블로그) - https://koonsland.tistory.com/139 <br>
  *-* ${}의 보안상 문제점 해결방안 - https://blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=forioso&logNo=220991757267&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView <br>
  *-* 다른 mapper 파일의 **resultMap 재사용**(참조) - https://finkle.tistory.com/82 <br>
  *-* reuse resultMap (stackoverflow) - https://stackoverflow.com/questions/13501069/reusing-mybatis-resultmap-in-multiple-mapper-xml <br>


  
