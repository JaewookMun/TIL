## Encryption


### algorithm
<br>

* MD (Message-Digest algorithm) : 암호화 해시 함수
  - 임의의 길이의 메시지를 입력받아, 일정한 길이의(128비트) 고정 출력값 반환
  - MD5를 보안관련 용도로 사용하는 것은 권장하지 않음 (SSL 인증서 변조 가능)
  > MD2, MD5
* SHA (Secure Hash Algorithm) : 단방향 해시 알고리즘
  > SHA-1, SHA-256, SHA-512

<br>
 Q: MD5 vs SHA-256 - difference?


<br>

### Java API class

* MessageDigest : Message Digest 알고리즘 제공
  
``` java
String str = "sample";
byte[] bytes = str.getBytes();

MessageDigest md = MessageDigest.getInstance("SHA-256");
md.update(bytes);

return md.digest(); // 암호화된 결과 반환

```


* commons-codec : Base64

### 플러스

* String.getBytes() : 문자열을 인코딩 후 바이트 배열로 반환 <br>
  -> 구현 프로세스 확인


<br>

* [참고] <br>
  *-*  Message Digest 알고리즘 이름 목록 - https://docs.oracle.com/en/java/javase/16/docs/specs/security/standard-names.html#messagedigest-algorithms <br>
  *-* String.getBytes()'s defualt charset - https://codingdog.tistory.com/entry/getBytes-String%EC%9D%84-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9D%B8%EC%BD%94%EB%94%A9%ED%95%98%EA%B3%A0-%EB%94%94%EC%BD%94%EB%94%A9-%ED%95%A0%EA%B9%8C <br>
  
