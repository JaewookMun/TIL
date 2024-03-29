# Shell Script (셸 스크립트)

<br>

### **작성방법**
  * 맨 첫줄은 #!/bin/bash 를 작성한다.
  
    ``` shell 
    #!/bin/bash

    # example

    REPOSITORY=/home/ec2-user/app/step2
    PROJECT_NAME=springboot

    cd $REPOSITORY/$PROJECT_NAME/

    ```

<br>

  * 자주 사용하는 vi, vim 명령어 및 단축키
    - 맨 앞줄 이동 : gg
    - 맨 끝줄 이동 : G
    - 검색 : /{searchKeyword}<br>
    -> n : 다음 항목으로 이동<br>
    -> N : 이전 항목으로 이동<br>
    - :noh = 문서에서 하이라이트 제거
    - 블록 주석처리 : norm i#
    - 블록 주석해제 : norm 1x


<br><br><br>



<br><br><br>

### .vimrc

* 줄 번호 표시 방법
  :set number / :set nonumber

* .vimrc가 적용  안될 때 root 에 작성하여 설정정보를 적용한다.
  vim --version 을 사용해서 사용자 정의를 위한 .vimrc 파일 위치를 확인할 수 있다.



<br><br><br>
<br><br><br>
<br><br><br>



[Bash 기본 문법]
---

<br>

## 특수문자 (special symbols)

<br>

### $number, $?

$number : bash 실행 시 함께 입력한 파라미터를 의미
$? : 1. bash shell에서 최근 실행한 명령어의 종료 스테이터스를 가진 변수, 2. 최근 실행한 함수의 return 값을 가진 변수 (정상 : 0)



<br>

### Single quotation['] vs Double quotation ["]
simplely :  Single quotation으로 감싼 것은 모두 String으로 인식 / Double quotation은 내부 String을 해석하여 인식


### backticks[\` `] vs braces[$( )]

Using backticks is deprecated.


<br><br><br>

## printf




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
<br><br><br>


### 여러개의 명령어를 한줄에서 실행하는 방법

- 세미콜론(';') <br>
  여러개의 명령어를 세미콜론으로 구분하여 한 줄에 나열하면 각 명령어가 순차적으로 실행된다.
  
  ``` bash
    // command1 ; command2 ; command3
    $ echo "Hello," ; echo "world!" ; date
  ```

<br>

- 더블 앰퍼샌드('&&') <br>
  여러 개의 명령어를 더블 앰퍼샌드로 구분하여 한 줄에 나열하면, 앞선 명령어가 성공적으로 실행될 경우에만 다음 명령어가 실행된다.

  ``` bash
    // command1 && command2 && command3
    $ apt update && apt upgrade && reboot
  ```

<br>

- 파이프 ('|') <br>
  파이프를 사용하여 한 명령어의 출력을 다음 명령어의 입력으로 전달할 수 있다.

  ``` bash
    // command1 | command2 | command3
    $ ls | grep "keyword" | wc -l
  ```





<br><br><br>
<br><br><br>


### Array

declare 

Array -> Associative Array vs Indexed Array

shell에서 Associative Array는 hash table 기준으로 정렬됨.
indexed array처럼 값을 넣은 순서대로 interator 작업을 처리할 수 없다.

<br><br>

배열을 사용해서 값을 저장하고 사용할 때 쌍따옴표(double quotation)를 적절히 사용하지 않으면 원하는 결과값을 얻을 수 없다.

``` bash

declare -a arr

arr+=("apple 1000")
arr+=("banana 2000")


for element in "${arr[@]}"
do
  ...
  ...
done

```
<br>

위와 같은 스크립트를 작성할 때, 배열에 넣는 요소에 쌍따옴표를 넣는 것도 중요하지만 for 문에 위치한 배열 표현식 역시 쌍따옴표로 감싸줘야한다. <br>
(삽입되는 요소에 space를 두기 위해 배열에 넣는 요소에 쌍따옴표를 사용)



<br><br><br>


### awk

awk는 입력데이터를 행(record)과 열(field)로 인식한다.

예시) docservice_pid=$( ps -ef | grep ./docservice | grep root | awk '$3 == 1 {print $2}')
>> 3번째 필드값이 1인 레코드의 2번째 필드를 출력하여 docservice_pid에 대입



<br><br><br>
<br><br><br>

### Key 기반 SSH 접속 인증(타 서버에 명령어 사용 시 비밀번호 입력 X)

<br>

- 비밀번호 프롬프트를 피하고 비밀번호 입력 없이 ssh 접근을 하는 방법

- 키 생성 : 로컬 시스템에서 키 생성
  
  ``` bash
    $ ssh-keygen -t rsa -b 4096 -f ~/.ssh/my_key  //명령어
      ...
      Enter passphrase (empty for no passphrase): //아무것도 입력하지 않아도 됨
      Enter same passphrase again:                //아무것도 입력하지 않아도 됨

  ```
  -> ssh-keygen 명령어를 수행하면 키에 대한 비밀번호를 요청하는데 아무것도 입력하지 않아도 상관없다.
  -> 위 명령어 수행 시 ~/.ssh/ 디렉토리에 'my_key'(private key), 'my_key.pub'(public key)가 생성된다.

<br>

- 공개 키 복사 : 공개 키를 원격 서버에 복사하여 비밀번호 없이 접근할 수 있도록 처리
  
  ``` bash
    $ ssh-copy-id -i ~/.ssh/my_key.pub username@remote_server_ip //원격 서버 정보
  ```
  -> 위 명령어를 실행하면 로컬 시스템의 공개 키가 원격 서버의 ~/.ssh/authorized_keys 파일에 추가 <br>
  -> username은 원격 서버의 사용자 이름이고, remote_server_ip는 원격 서버의 IP 주소 또는 도메인 이름을 나타냄. <br>
  -> 처음 실행 시 원격 서버의 암호를 입력해야 원격 서버에 공개 키를 복사할 수 있음.

<br>

- 비밀번호 없이 접근 : PEM 키를 통해 비밀번호 없이 원격 서버에 접근가능
  
  ``` bash
    ssh -i ~/.ssh/my_key username@remote_server_ip
  ```
  -> pem 키를 사용해서 원격 서버에 접근하기 때문에 비밀번호 프롬프트 발생 없이 바로 접근 가능. <br>
  -> pem 키를 안전하게 관리하고 접근을 제한하는 것이 중요. <br>
  [참고] 공개키를 원격 서버에 등록하고 접근할 때는 개인키를 사용해 접근한다.


  ※ 보안 특성을 고려하여 sshpass는 사용하지 않는다.

<br>

- sudo 사용방법 <br>
  Key 접근 방식을 사용해 sudo 가 필요한 명령어 수행 시 아래와 같은 error 메시지가 나타날 수 있다. <br>
  sudo: a terminal is required to read the password; either use the -S option to read from standard input or configure an askpass helper <br>
  에러 메시지에서 확인할 수 있는 것처럼 sudo 의 -S 옵션을 활용해 문제를 해결할 수 있다. <br>

  ``` bash
    $ echo 'password' | ssh -i ~/.ssh/my_key username@remote_server_ip "sudo -S ls -al"
  ```
  -> -S, --stdin : read password from standard input


<br><br><br>
<br><br><br>


### [참고] <br>
  * **vi/vim editor 설정** <br>
  *-* .vimrc 설정방법 - https://github.com/johngrib/simple_vim_guide/blob/master/md/vimrc.md <br>
  *-* 줄번호 표시 방법 - https://jjeongil.tistory.com/1728?category=686032 <br>
  *-* ~/.vimrc가 적용되지 않을 때 해결방법 (root 적용) - https://stackoverflow.com/questions/28235592/vimrc-settings-for-user-dont-work-for-root <br>

  <br>

  * special character <br>
  *-* what is '$1' > shell script 파라미터 - https://bash.cyberciti.biz/guide/$1 <br>
  *-* '$?' > exit status or function return - https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_$%3F <br>


  * bash 문법 <br>
  *-* difference between single(') and double(") quotation - https://stackoverflow.com/questions/6697753/difference-between-single-and-double-quotes-in-bash <br>
  *-* when should I wrap quotes around a shell variable - https://stackoverflow.com/questions/10067266/when-should-i-wrap-quotes-around-a-shell-variable <br>
  *-* backticks vs braces (1) - https://stackoverflow.com/questions/22709371/backticks-vs-braces-in-bash <br>
  *-* backticks vs braces (2) - http://mywiki.wooledge.org/BashFAQ/082 <br>
  *-* boolean 값 변수에 넣고 사용하는 방법 [@@@@@] - https://stackoverflow.com/questions/9906041/bash-boolean-expression-and-its-value-assignment <br>
  *-* multiple - https://www.log2base2.com/shell-script-examples/operator/shell-script-for-multiplication-of-two-numbers.html <br>
  

  <br>

  * printf <br>
  *-* printf document [w3big.com] - http://www.w3big.com/ko/linux/linux-shell-printf.html <br>
  *-* how to use printf for alignment 1 [column] - https://stackoverflow.com/questions/4409399/padding-characters-in-printf <br>
  *-* how to use printf for alignment 2 - https://unix.stackexchange.com/questions/660110/how-to-align-the-output-generated-in-a-shell-for-loop-by-columns <br>

  <br>

  * **function** <br>
  *-* 함수 return 값 대체하는 방법 (echo, exit status, variable) - https://stackoverflow.com/questions/8742783/returning-value-from-called-function-in-a-shell-script <br>


  <br>

  * **Array in bash** <br>
  *-* 배열 사용방법 (**tutorial**) - https://linuxconfig.org/how-to-use-arrays-in-bash-script <br>
  *-* declare command in bash - https://unix.stackexchange.com/questions/510220/what-is-declare-in-bash <br>
  *-* [declare -a vs -A] indexed Array vs associative Array - https://stackoverflow.com/questions/28179409/bash-array-assignment-fails-if-you-declare-the-array-in-advance <br>
  *-* 연관배열(associativee array)란? - https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B4%80_%EB%B0%B0%EC%97%B4 <br>
  *-* associative array order [stackoverFlow] - https://stackoverflow.com/questions/29161323/how-to-keep-associative-array-order <br>
  *-* array and double quotation - https://stackoverflow.com/questions/9084257/bash-array-with-spaces-in-elements <br>


  <br>

  * loop <br>
  *-* for loop 사용법 정리 블로그 - https://jhnyang.tistory.com/191 <br>

  <br>

  * If statement <br>
  *-* if문 조건 정리 블로그(1) - https://jink1982.tistory.com/48 <br>
  *-* if문 조건 정리 블로그(2) - https://lxstitch.tistory.com/65 <br>

  <br>

  * String Edit <br>
  *-* 콤마(,) 제거하기 (sed, awk 사용) - https://stackoverflow.com/questions/39285636/how-to-remove-last-comma-from-line-in-bash-using-sed-or-awk <br>
  *-* awk 사용방법 레코드(행), 필드(열) - https://veneas.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%8C%EC%9D%BC%EC%9D%98-%EC%9B%90%ED%95%98%EB%8A%94-%ED%96%89%EA%B3%BC-%EC%97%B4-%EC%B6%9C%EB%A0%A5-awk <br>
  
  * sed <br>
  *-* sed 명령어 정리 - https://jhnyang.tistory.com/287 <br>

  <br>

  * etc <br>
  *-* file download 시 저장 없이 스크립트를 시작하는 방법 - https://askubuntu.com/questions/891872/pipe-to-sudo-e-bash <br>
  *-* sudo with redirection in bash (echo ~~ > ~.file) - https://askubuntu.com/questions/230476/how-to-solve-permission-denied-when-using-sudo-with-redirection-in-bash <br>
  (꺽은 괄호를 ubuntu에서 redirection 이라고 표현함.)
