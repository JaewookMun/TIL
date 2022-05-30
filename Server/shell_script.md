# Shell Script (셸 스크립트)

<br>

## **작성방법**
  * 맨 첫줄은 #!/bin/bash 를 작성한다.
``` bash 
#!/bin/bash

# example

REPOSITORY=/home/ec2-user/app/step2
PROJECT_NAME=springboot

cd $REPOSITORY/$PROJECT_NAME/

```

cf. 자주 사용하는 vi, vim 단축키
맨 앞줄 이동 : gg
맨 끝줄 이동 : G

검색 : /{searchKeyword}
  - n : 다음 항목으로 이동 
  - N : 이전 항목으로 이동
  - :noh = 문서에서 하이라이트 제거



<br><br><br>

## vi/vim 명령어

블록 주석처리 / 해제
norm !#
norm 1x



<br><br><br>

### .vimrc

* 줄 번호 표시 방법
  :set number / :set nonumber




<br><br><br>
<br><br><br>
<br><br><br>

Bash 기본 문법
---

<br><br>

## backticks[\` `] vs braces[$( )]

Using backticks is deprecated.




<br><br><br>
<br><br><br>

## if statement

* **기본 if 문**
  * if [조건] then 수행 명령 fi 구조이며, 'fi'는 if문의 종료를 의미한다.
    c.f. - finished

``` bash
if [조건]; then
  수행할 명령
fi
```




* **if elif else 문**
  * else를 제외하고 기본 if문과 동일

``` bash
if [조건]; then
  수행할 명령
elif [조건]; then
  수행할 명령
fi

```


* **if else 문**
  * else를 제외하고 기본 if문과 동일

``` bash
if [조건]; then
  수행할 명령
else
  수행할 명령
fi

```



<br><br><br>


declare


### Array





<br><br><br>
<br><br><br>


### [참고] <br>
  * **vi/vim editor 설정** <br>
  *-* .vimrc 설정방법 - https://github.com/johngrib/simple_vim_guide/blob/master/md/vimrc.md <br>
  *-* 줄번호 표시 방법 - https://jjeongil.tistory.com/1728?category=686032 <br>
  
  <br>

  * bash 문법 <br>
  *-* difference between single(') and double(") quotation - https://stackoverflow.com/questions/6697753/difference-between-single-and-double-quotes-in-bash <br>
  *-* when should I wrap quotes around a shell variable - https://stackoverflow.com/questions/10067266/when-should-i-wrap-quotes-around-a-shell-variable <br>

  *-* backticks vs braces (1) - https://stackoverflow.com/questions/22709371/backticks-vs-braces-in-bash <br>
  *-* backticks vs braces (2) - http://mywiki.wooledge.org/BashFAQ/082 <br>

  <br>
  
  * **bash array** <br>
  *-* 배열 사용방법 (**tutorial**) - https://linuxconfig.org/how-to-use-arrays-in-bash-script <br>
  
  *-* declare command in bash - https://unix.stackexchange.com/questions/510220/what-is-declare-in-bash <br>
  *-* [declare -a vs -A] indexed Array vs associative Array - https://stackoverflow.com/questions/28179409/bash-array-assignment-fails-if-you-declare-the-array-in-advance <br>
  *-* 연관배열(associativee array)란? - https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B4%80_%EB%B0%B0%EC%97%B4 <br>
  *-* associative array order [stackoverFlow] - https://stackoverflow.com/questions/29161323/how-to-keep-associative-array-order <br>


  <br>
  
  *-* for loop 사용법 정리 블로그 - https://jhnyang.tistory.com/191 <br>
  *-* if문 조건 정리 블로그 - https://jink1982.tistory.com/48 <br>

  


