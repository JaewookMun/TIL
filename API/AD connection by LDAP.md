# Active Directory

###### AD (Active Directory)
- 도메인 형태의 트리 구조로 정보 객체를 저장
- 사용자가 원하는 정보를 쉽고 빠르게 찾거나 제어할 수 있도록 자원을 관리하는 서비스의 개념
    *>* Active Directory는 네임 스페이스에 따라 디렉토리 서비스를 제공
    이때, 네임 스페이스는 도메인 시스템(DNS - Domain Name System)의 형태를 그대로 따른다.
- 구조 : 포레스트 > 트리 > 도메인 > 조직단위(OU)


<br>

  _*_ **디렉토리**(Directory) - 체계적인 설계를 통해 정보자원을 질서정연하게 담은 정보 저장소(Information Storage Location)

  _*_ **네임스페이스**(NameSpace) - 프로그래밍 언어에서 특정한 객체(Object)를 이름(Name)에 따라 구분할 수 있는 범위를 의미

<br>

## **LDAP**
  *-* 경량 디렉터리 액세스 프로토콜(영어: Lightweight Directory Access Protocol; LDAP)은 TCP/IP 위에서 디렉터리 서비스를 조회하고 수정하는 응용 프로토콜이다.
  *-* default character-set: **UTF-8**
  *-* LDAP로 가져올 수 있는 결과의 기본 최대값은 1000개 - 증가시키기 위해서는 AD 서버에서 MaxPageSize의 값을 증가시켜야함
      > Java api로 paing 처리 개념으로 모두 가져올 수 있음.

<br>

* 클래스 및 인터페이스
  - LdapContext : LDAPv3 스타일 컨트롤을 사용하여 작업을 수행하고 LDAPv3 스타일 확장 작업을 수행할 수 있는 컨텍스트
  - InitialLdapContext : LDAPv3 스타일 확장 조작 및 제어를 수행하기 위한 시작 컨텍스트

<br>

* Connection of AD through LDAP

<br>

* SearchControl - LDAP 통신으로 검색할 자원의 검색조건 제어를 설정한다고 볼 수 있다.

<br>

* **AD attributes**
  - objectGUID* : AD 객체가 갖는 고유값으로 변경할 수 없다. (고유 식별자)
    > GUIDs are assigned to every object created by Active Directory, not just User and Group objects. <br> Each object's GUID is stored in its Object-GUID (objectGUID) property.

    objectGUID는 2진 데이터(binary data)이기 때문에 LDAP로 읽은 값을 그대로 출력하면 확인할 수 없다.
    Base64 방식(64진법 - ASCI II)으로 읽을 수 있는 데이터로 변환하여 값을 활용.
<br>

  - distinguishedName : 콤마로 연관 식별자들을 연결한 식별 정보 속성 <br>
    *>* 'attribute=value' 형태로 관련 값들을 갖는다. (UTF-8) (RDN - relative distinguished names) 
    <br>
    ex) DC - domainComponent, OU - organizationUnitName, CN - commonName, etc.
<br>

  - sAMAccountName : 도메인 내부에서는 고유값이지만 전역(포레스트)에서는 중복될 수 있다.
<br>

  - displayName : 화면에 보이는 이름 (중복이 가능하며 식별자가 될 수 없다.)

  _*_ GUID stands for **Globally Unique Identifier** <br>

  _*_ unicodePwd : 암호화된 NT hash 값에 대한 속성 <br>
  _*_ dbcsPwd : 암호화된 LM hash 값에 대한 속성 <br>
  [참고]
  unicodePwd 속성을 통해 비밀번호를 변경할 수는 있지만 읽어올 수 없음. <br>
  AD passwords (just like Windows ones) are stored using non-reversible encryption, so the standard answer is a definite "NO".
  _*_ AD password는 hash로 OWF(One-Way Function)으로 암호화 됨

* SearchResult
  

<br>

* AD viewer and editor : **AdExplorer.exe** (접근 정보가 있을 때 활용 - Microsoft 프로그램)


<br>

### [참고] <br>

  * Directory Service <br>
  *-* AD 및 DNS 기본 개념(Name Space) **check** - https://mapoo.net/os/oswindows/%EC%97%91%ED%8B%B0%EB%B8%8C-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC-%EA%B5%AC%EC%A1%B0%EC%9D%98-%EC%9D%B4%ED%95%B4/ <br>
  *-* LDAP in 위키 - https://ko.wikipedia.org/wiki/LDAP <br>
  *-* LDAP 개념 분석 - https://yongho1037.tistory.com/796 <br>

  <br>

  * LDAP 스키마 - LDAP 디렉토리 항목에 대한 속성
  *-* LDAP 스키마(구조) - https://help.hcltechsw.com/domino/11.0.1/ko/admin/conf_ldapschema_c.html <br>
  *-* LDAP 스키마 구조 속성 설명 - https://support.google.com/cloudidentity/answer/9188164?hl=ko <br>
  *-* AD 검색 개념 (Microsoft ~ eng) - https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc978021(v=technet.10) <br>

  <br>

  * Java api 활용
  *-* Java JNDI api - https://deviscreen.tistory.com/123 <br>
  *-* LDAP 연결 방법 소스 예시1 - https://black-whisker.tistory.com/32 <br>
  *-* LDAP 연결 방법 소스 예시2 - https://stackoverflow.com/questions/8551809/how-to-connect-with-java-into-active-directory <br>
  *-* LDAP 연결 방법 소스 예시3 - https://qmffjem09.tistory.com/entry/java-ldap-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D <br>
  *-* initialLdapContext 설명 (doc) - https://runebook.dev/ko/docs/openjdk/java.naming/javax/naming/ldap/initialldapcontext <br>

  <br>

  * 검색조건 설정
  *-* LDAP 통신 search base 설명 - https://www.watchguard.com/help/docs/help-center/en-US/Content/en-US/Fireware/authentication/find_ad_search_base_c.html <br>
  *-* LDAP 검색필터(search filter) 작성법 - https://confluence.atlassian.com/kb/how-to-write-ldap-search-filters-792496933.html <br>
  *-* LDAP 검색필터 (Microsoft ~ kor) - https://docs.microsoft.com/ko-kr/windows/win32/adsi/search-filter-syntax?redirectedfrom=MSDN <br>
  *-* 검색결과 최대값 - https://social.msdn.microsoft.com/Forums/sqlserver/en-US/58a5326b-e344-4eb6-97a1-bb68f7b1292f/ldap-data-load-failed-after-loading-1000-records?forum=sqlintegrationservices <br>
  *-* 검색결과 최대값(MaxPageSize) 증가시키는 법 - https://bono915.tistory.com/entry/Ldap-How-to-get-more-than-1000-records-in-querying-AD <br>

  <br>

  * LDAP 스키마 속성 개념 - Returningattributes
  *-* objectGUID의 특성 [binary data] https://stackoverflow.com/questions/18383843/how-do-i-convert-an-active-directory-objectguid-to-a-readable-string <br>
  *-* is objectGUID unique ? - https://serverfault.com/questions/105486/is-the-objectguid-unique-and-will-it-ever-change <br>
  *-* Base64란 ? 설명 - https://devuna.tistory.com/41 <br>
  *-* AD 사용자 이름 특성 (로그인 ID) [AD속성] (Microsoft ~ kor) - https://docs.microsoft.com/ko-kr/windows/win32/ad/naming-properties <br>
  *-* **AD 식별자** (Distinguished Names) [Microsoft] - https://docs.microsoft.com/en-us/previous-versions/windows/desktop/ldap/distinguished-names <br>
  *-* 두 속성(name, displayName) 간 차이점 - https://www.reddit.com/r/activedirectory/comments/7zqys7/difference_between_name_and_displayname_fields/ <br>
  *-* MS > SID vs GUID - https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc961625(v=technet.10)?redirectedfrom=MSDN <br>
  *-* password cann't be read in plain text - https://serverfault.com/questions/292767/any-way-to-see-an-active-directory-password <br>
  *-* AD 및 Windows 비밀번호 저장방법 (암호화 [OWF, one-way function]) - https://docs.microsoft.com/ko-kr/windows-server/security/kerberos/passwords-technical-overview <br>

  <br>
  
  * 검색결과 처리
  *-* SearchResult 설명 (doc) - https://runebook.dev/ko/docs/openjdk/java.naming/javax/naming/directory/searchresult <br>
  *-* **DN 조작** (LdapName) - https://docs.oracle.com/javase/tutorial/jndi/newstuff/ldapname.html <br>
  *-* AD 1000개 이상 조회하기 - https://stackoverflow.com/questions/11311765/ldap-how-to-return-more-than-1000-results-java <br>
  
   

  * 관련 응용 프로그램
  *-* Active Directory Download link - https://docs.microsoft.com/en-us/sysinternals/downloads/adexplorer <br>



