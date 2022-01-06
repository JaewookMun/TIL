## Active Directory

* AD (Active Directory)




  _*_ 네임스페이스(NameSpace) - 프로그래밍 언어에서 특정한 객체(Object)를 이름(Name)에 따라 구분할 수 있는 범위를 의미

<br>

* LDAP
  *-* 경량 디렉터리 액세스 프로토콜(영어: Lightweight Directory Access Protocol; LDAP)은 TCP/IP 위에서 디렉터리 서비스를 조회하고 수정하는 응용 프로토콜이다.
  *-* default character-set: **UTF-8**

<br>

* 클래스 및 인터페이스
  - LdapContext : LDAPv3 스타일 컨트롤을 사용하여 작업을 수행하고 LDAPv3 스타일 확장 작업을 수행할 수 있는 컨텍스트
  - InitialLdapContext : LDAPv3 스타일 확장 조작 및 제어를 수행하기 위한 시작 컨텍스트

<br>

* Connection of AD through LDAP

<br>

* **AD attributes**
  - objectGUID* : AD 객체가 갖는 고유값으로 변경할 수 없다. (고유 식별자)
    > GUIDs are assigned to every object created by Active Directory, not just User and Group objects. <br> Each object's GUID is stored in its Object-GUID (objectGUID) property.
<br>

  - distinguishedName : 콤마로 연관 식별자들을 연결한 식별 정보 속성 <br>
    *>* 'attribute=value' 형태로 관련 값들을 갖는다. (UTF-8) (RDN - relative distinguished names) 
    <br>
    ex) DC - domainComponent, CN - commonName, OU - organizationUnitName, etc.
<br>

  - sAMAccountName : 도메인 내부에서는 고유값이지만 전역(포레스트)에서는 중복될 수 있다.
<br>

  _*_ GUID stands for **Globally Unique Identifier**


* SearchResult
  

<br>

* AD viewer and editor : **AdExplorer.exe** (접근 정보가 있을 때 활용 - Microsoft 프로그램)


<br>

* [참고] <br>
  *-* LDAP in 위키 - https://ko.wikipedia.org/wiki/LDAP <br>
  *-* AD 및 DNS 기본 개념(Name Space) **check** - https://mapoo.net/os/oswindows/%EC%97%91%ED%8B%B0%EB%B8%8C-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC-%EA%B5%AC%EC%A1%B0%EC%9D%98-%EC%9D%B4%ED%95%B4/ <br>
  *-* AD와 LDAP의 차이점 - https://m.blog.naver.com/sung_mk1919/221824347182 <br>
  *-* LDAP 스키마(구조) - https://help.hcltechsw.com/domino/11.0.1/ko/admin/conf_ldapschema_c.html <br>
  *-* AD와 DNS의 개념 https://sbck.tistory.com/25 <br>
  *-* AD DN 개념 (Microsoft ~ eng) - https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc978021(v=technet.10) <br>
  *-* Java JNDI api - https://deviscreen.tistory.com/123
  *-* LDAP 연결 방법 소스 예시1 - https://black-whisker.tistory.com/32 <br>
  *-* LDAP 연결 방법 소스 예시2 - https://stackoverflow.com/questions/8551809/how-to-connect-with-java-into-active-directory <br>
  *-* LDAP 연결 방법 소스 예시3 - https://qmffjem09.tistory.com/entry/java-ldap-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D <br>
  *-* LDAP 통신 search base 설명 - https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Fireware/authentication/find_ad_search_base_c.html <br>
  *-* LDAP 검색필터(search filter) 작성법 - https://confluence.atlassian.com/kb/how-to-write-ldap-search-filters-792496933.html <br>
  *-* LDAP 검색필터 (Microsoft ~ kor) - https://docs.microsoft.com/ko-kr/windows/win32/adsi/search-filter-syntax?redirectedfrom=MSDN <br>
  *-* AD 사용자 이름 특성 [AD속성] (Microsoft ~ kor) - https://docs.microsoft.com/ko-kr/windows/win32/ad/naming-properties <br>
  *-* AD 식별자 (Distinguished Names) - https://docs.microsoft.com/en-us/previous-versions/windows/desktop/ldap/distinguished-names <br>
  *-* initialLdapContext 설명 (doc) - https://runebook.dev/ko/docs/openjdk/java.naming/javax/naming/ldap/initialldapcontext <br>
  *-* SearchControl 설명 (doc) - https://runebook.dev/ko/docs/openjdk/java.naming/javax/naming/directory/searchcontrols <br>
  *-* is GUID unique ? - https://serverfault.com/questions/105486/is-the-objectguid-unique-and-will-it-ever-change <br>
  *-* MS > SID vs GUID - https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961625(v=technet.10)?redirectedfrom=MSDN <br>



