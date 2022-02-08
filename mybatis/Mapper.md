# Mapping (맵핑)

## Parameter

* 2개 이상의 파라미터를 맵핑하는 방법
  - VO, Map, @Param 사용


* 다른 .xml 파일에 있는 resultMap 을 재사용할 수 있다.
  -> namespace.id 형태로 다른 mapper 파일의 resultMap을 참조

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


* [참고] <br>
  *-* MyBatis 공식 페이지 - https://mybatis.org/mybatis-3/ko/sqlmap-xml.html#insert_update_and_delete <br>
  *-* 다른 mapper 파일의 **resultMap 재사용**(참조) - https://finkle.tistory.com/82 <br>
  *-* reuse resultMap (stackoverflow) - https://stackoverflow.com/questions/13501069/reusing-mybatis-resultmap-in-multiple-mapper-xml <br>


  
