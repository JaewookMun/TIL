# Linux

서버 spec (장치, cpu, memory) 확인 커맨드
```
$ cat /proc/meminfo
$ cat /proc/cpuinfo

```


apt 설치시 발생 가능한 encryt 인증서 문제 (mariadb - apt update)
https://hamonikr.org/hamoni_board/106932
https://www.bearpooh.com/100

apt repository 제거방법 - https://blkcoding.blogspot.com/2017/12/repository-apt-update.html <br>
<br>

## Kernel

하드웨어와 소프트웨어를 연결
---

운영체제의 가장 하단에 위치한다. 운영체제의 핵심이 되는 프로그램으로 운영체제에서 사용하는 모든 프로그램은 커널 프로그램을 기반으로 동작한다.

![kernel_architecture](./img/kernel_architecture.png)
(응용 소프트웨어를 컴퓨터 하드웨어(cpu, memory, devices)에 연결)



<br><br><br>
<br><br><br>

## Linux Configuration (파일시스템)

LVM : dynamic partitions, meaning that you can create/resize/delete LVM "partitions" (they're called "Logical Volumes" in LVM-speak) from the command line while your Linux system is running: no need to reboot the system to make the kernel aware of the newly-created or resized partitions.



<br><br><br>
<br><br><br>

### 파일시스템과 파티션

* 파일시스템 : 파일을 저장하기위한 논리적인 구조
* 디스크 파티션 : 물리적인 디스크를 논리적인 저장영역으로 분할하는 것



<br><br>

### VMware의 네트워크 모드

VMware의 네트워크 모드는 세가지(NAT, Bridge, Host Only)가 있으며 주로 NAT 모드를 사용한다.




<br><br>

### VMware에 Linux 설치하기

VMDK 파일 생성방식
- Store virtual disk as a single file : 
- Split virtual disk into multiple files : 다른 컴퓨터로 옮길 때 더 편리함.


<br><br>

SSH vs OpenSSH

SSH(Secure SHell)는 컴퓨터간에 안전하게 데이터를 전달할 수 있도록 규정한 프로토콜이다.
OpenSSH는 SSH 프로토콜을 구현한 오픈소스이며 리눅스에서 SSH server & client로 주로 사용된다.
(참고: 인터페이스와 구현체 관계)

apt-get install ssh  |  **apt-get install openssh(-server)**  > 둘은 같은 명령어나 마찬가지이다. (서로 의존관계로 연관되어 있음.)



Ubuntu의 패키지 정보가 제공되는 웹사이트에서 ssh 팩키지와 Openssh 패키지의 다운로드 소스 팩키지는 'openssh'로 서로 같다.
[check]: 'Other Packages Related to ssh', Download Source Package openssh
(웹프로그래밍 관점에서 인터페이스 팩키지를 다운받음으로서 구현체인 OpenSSH를 받는다고 생각할 수 있음)

<br>

![](./img/install_ssh.png)

> 1. Install ssh
> 2. Read package lists
> 3. Build dependency tree
> 4. (after yes) install other packages like openssh-server, etc




<br><br><br>

systemctl status ssh로 프로세스 상태를 확인해보면 OpenBSD Secure Shell server가 실행중인 것을 확인할 수 있다.
> sudo systemctl status ssh





<br><br><br>

## 방화벽 설정 (firewall)

서버 통신의 in/out-bound 통신의 포트번호, IP 주소 등을 허용하기 위해서는 방화벽 정보를 설정해야한다.
리눅스에서는 iptables, ufw로 방화벽을 설정할 수 있다.
(iptables와 ufw는 유사한 기능을 가지고 있으며 사용법이 복잡한 iptables와 달리 ufw는 간편하게 사용할 수 있다.)

* iptables : 사용법이 복잡하고 ufw에 비해 정교한 설정을 하기 위해 사용한다.

* ufw(Uncomplicated FireWall) : 복잡한 iptables에 비해 사용법이 간편하다. 간단하게 방화벽을 설정 할 수 있다.

allow, deny 설정
- sudo ufw allow <port>/<protocol>
- sudo ufw deny <port>/<protocol>
- tcp/udp 한번에 허용 하려면 port 번호만 표기하면 됨.

> sudo ufw allow 20/tcp (tcp 프로토콜을 사용한 20번 포트 허용)
> sudo ufw allow 20 (20번 포트에 대하여 tcp, udp 프로토콜 모두 허용)




<br><br><br>
<br><br><br>

## Process management

top (table of processes) : '작업 관리자 (task manager)' 프로그램, 장치(This device)에서 실행중인 프로세스 목록을 통해 CPU와 Memory 사용량을 확인할 수 있다. 




<br><br><br>
<br><br><br>

## 디스크 용량 관리




<br><br><br>
<br><br><br>

## Linux 프로세스 메모리 확인하는 방법

cd ~/ps_mem/
sudo ./ps_mem.py

![process_memory](./img/process_memory.JPG)



<br><br><br>
<br><br><br>


## NTP (Network Time Protocol) 설정

1) systemd-timesyncd
  (installed in 'Ubuntu 배포판') <br>

  config file location : /etc/systemd/timesyncd.conf

  blog link 1 - https://velog.io/@markyang92/systemd-%EC%8B%9C%EA%B0%84-%EB%8F%99%EA%B8%B0%ED%99%94 <br>



<br><br><br>

2) NTP package 설치 <br>
  blog link 1 - https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-NTP-%EC%8B%9C%EA%B0%84-%EB%8F%99%EA%B8%B0%ED%99%94-%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-Ubuntu <br>
  blog link 2 - https://whitewing4139.tistory.com/132 <br>




<br><br><br>
<br><br><br>

## 프로세스
--

## 시작 프로세스 - 서비스 등록 : init, systemd

init 프로세스

부팅이 시작되면 사용자 영역에서 최초로 시작되는 프로세스

* init.d : init 프로세스가 실행되기 위한 스크립트 파일들이 나뉘어서 보관된 곳
  (프로그램 하나를 설치하면 기동, 종료스크립트가 init.d 디렉토리에 설치되었음. **systemd로 대체**)

<br>


**Systemd**

* init 프로세스에서 개선된 프로세스
* pid1
* 시스템 전반에 영향을 끼침
* linux가 부팅되는 과정에서 시스템을 초기화하고 환경설정을 해주는 역할
* 시스템 부팅 동안의 과정들을 병렬화하여 동작

init, systemd 를 통해서 서비스 등록을 할 수 있다.
> sudo service tomcat9 start

c.f.) systemctl (서비스 제어 명령어)

service 명령어는 **systemctl**의 wrapper script다.





<br><br><br>

### nohup









<br><br><br>
<br><br><br>
<br><br><br>

## 명령어



<br><br><br>

## 서비스 제어 명령어



<br><br>

ls

ls는 해당 디렉토리에 위치한 파일/디렉토리 정보를 제공하며 ll은 ls 명령어에 [-l] 옵션을 준 명령어를 의미
> ll = ls -l

_*_ ll은 sudo 키워드와 함께 사용할 수 없지만 ls -l은 sudo와 함께 사용할 수 있음

<br><br>

파일 / 디렉토리 갯수 확인하는 방법

```
ls -l | grep ^d | wc -l // 디렉토리 갯수

ls -l | grep ^- | wc -l // 파일 갯수

```


<br><br><br>

## 출력관련 명령어

grep
> grep -- -search_keyword
> : 더블 대시를 사용하여 대시문자를 검색할 수 있다.


> grep 메타문자
^ : 라인의 시작





<br><br>

wc (word count) : 사용자가 지정한 파일의 행, 단어, 문자수를 세는 프로그램

옵션 : -l (행), -w (단어), -c (문자)





<br><br>

awk (Aho Weinberger Kernighan) : 텍스트 파일 및 텍스트를 행과 열(row and column) 시스템을 이용해서 출력하는 명령어 (프로그램)
(awk로 출력하는 대상의 구조가 행렬의 형태로 표현될 때 각 줄(line)은 Record, 그 안의 단어들은 field로 표현된다. 이때, 필드는 공백으로 구분되어진다.)

사용법
> awk '패턴 {액션}'


``` linux
   ll | awk '{ print $9 }' | grep ^d 

```
설명: 파일 목록을 조회한 뒤 'd'로 시작하는 파일/디렉토리 명을 출력하는 명령


<br><br>

xargs : 여러줄 출력을 한줄로 출력



<br><br>

sed (stream editor) : 텍스트(파일)을 편집하고 원하는 데이터를 출력가능 - 문자열 변경 편집기

e.g) 문자열 대체


``` linux
   ll | awk '/[0-9]\// { print $9 }' | xargs echo | sed 's/\//,/g'

```
설명: 파일목록 조회한 결과에서 '숫자/' 패턴의 파일명을 필터링한 뒤 한줄로 출력한 결과에서 '/'를 ','로 변경하여 출력




<br><br><br>
<br><br><br>
<br><br><br>

## 다중 명령어

한 문장으로 단일 명령을 수행할 수 있지만 몇가지 명령어를 통해 여러 명령을 동시에 실행할 수 있다.

* ; [세미콜론] - 명령들을 구분하는데 사용하며 명령들간 영향을 받지 않는다. 실패 & 성공 조합 가능
* | [파이프] - 리눅스에서 파이프는 두 프로세스를 이어주는 역할을 함. '$ 명령A | 명령B' 는 '명령A'의 결과를 가지고 '명령B'를 수행한다는 의미 
* && [더블앤퍼센드] - 앞선 명령이 에러 없이 정상 종료되었을 때 뒷 명령이 실행 (세미콜론과의 차이)
* || [더블버티컬바] - 첫번째 명령의 결과가 에러가 발생했을 때 뒷 명령이 실행



<br><br><br>
<br><br><br>

## 권한 관리

리눅스는 멀티유저 시스템이기 때문에 파일/디렉토리에 접근할 수 있는 권한(**Permission**)이 존재

<br><br>

파일정보 보기 <br>
> $ ls -al  //현재 위치의 파일들을 자세히 보여주는 명령어

``` linux
drwxr-xr-x 3 root root 4096 2022-03-11 18:14 ./
drwxr-xr-x 3 root root 4096 2022-03-11 18:14 ../
drwxr-xr-x 3 root root 4096 2022-03-11 18:14 ROOT/
      ...
```

* 파일 Type : [d] - 디렉토리, [l] - 링크파일, [-] - 일반 파일, etc..
* **퍼미션 정보** : 해당파일에 어떤 퍼미션이 부여되어있는지 표시
* 링크수 : 해당 파일이 링크된 수 (윈도우의 바로가기와 동일)
* 소유자 : 해당 파일의 소유자 이름
* 소유그룹 : 해당 파일을 소유한 그룹 이름 (특별한 변경이 없으면 일반적으로 소유자가 속한 그룹이 소유그룹으로 지정되며 대부분 소유자 이름과 동일)
* 용량 : 파일 용량
* 생성날짜 : 파일 생성날짜
* 파일 이름





<br><br><br>
<br><br><br>

**권한(Permission, 퍼미션)**

<br>

권한(Permission) 종류  <br>
* 읽기(r) : 파일의 읽기 권한
* 쓰기(w)) : 파일의 쓰기 권한(생성, 수정, 삭제)
* 실행하기(x) : 파일의 실행 권한
<br> (디렉토리는 실행권한이 있어야 내부로 이동 가능)

<br>

사용자에 따른 권한 지정
* 소유자 : 소유자에 대한 권한 지정
* 그룹 : 소유 그룹에 대한 권한 지정
* 공개 : 다른 사용자에 대한 권한 지정

```
   eg.) d rwx r-x ---      소유자에게는 모든 권한이 존재, (rwx)
                           소유그룹에는 읽고 실행할 수 있는 권한 존재, (r-x)
                           다른 사용자는 아무 권한도 존재하지 않음. (---)

```


<br><br>

권한 변경하기

> chmod [변경될 권한값] [변경할 파일]

> 권한 값 구하는 방법
   * 각 권한 기호를 숫자로 변환 (r = 4, w = 2, x = 1 | 2진법 기반)
   예) r-x = 401 
   <br>

   * 변환한 숫자를 합산 예) 401 > 4+0+1 = 5
   
   이처럼 사용자에 따른 권한을 숫자값으로 변환하여 표기하며 디렉토리의 경우 [-R] 옵션을 주어 디렉토리의 모든 하위 파일 및 디렉토리의 권한을 변경할 수 있다. <br>

   if) 권한이 'rwxr-xr-x' 라면 4+2+1 | 4+0+1 | 4+0+1 = 755라는 권한 값을 의미



``` linux

   chmod 755 a.sh
   chmod -R 777 shell/

```



<br><br>

## 사용자 관리

- 원격으로 우분투 접속 시 root로 로그인하면 'Access denied' 메시지 발생 >> ssh 접속에 대한 root 접속권한 설정시 해결
  (일반 사용자 계정으로 접속해 su로 root 권한을 얻는 것은 가능하지만 처음부터 root로 로그인 하는 것은 막혀있음.)

  $ vi /etc/ssh/sshd_config
  PermitRootLogin 값을 yes로 수정
  ``` bash
  #PermitRootLogin prohibit-password
  PermitRootLogin yes

  ```

- root 권한을 얻기 위해 사용하는 명령어 su / su - / sudo 에는 차이점이 존재한다. root 권한을 위해 su / sudo 명령어를 사용할 때의 특징은 다음과 같다.
  a. su (Switch User) : root 사용자로 계정을 전환
  b. sudo (SuperUser DO) : root 계정의 권한을 빌림

<br><br><br>
<br><br><br>

### 사용자 추가

사용자 추가
adduser 명령어를 사용하면 자동으로 홈디렉토리가 생성되고 비밀번호를 설정할 수 있다.  (useradd 명령어는 이를 별도로 설정해줘야함.)

$ adduser {사용자}

사용자의 그룹을 변경하는 방법
$ usermod -aG {그룹} {사용자}

*참고 - usermod 에서 a 옵션을 제거하면 사용자의 기존의 그룹 정보는 제거됨에 따라 문제가 발생할 수 있으므로 기존 그룹정보는 포함한 상태에서 추가하기 위해서는 a옵션을 추가해준다.

temp 사용자에게 sudo 권한을 주고 관리자 그룹으로 포함시키는 예시
$ sudo usermod -aG sudo temp
$ sudo usermod -aG adm temp




<br><br><br>
<br><br><br>

## 그룹 관리

- Primary Group : 1개만 존재 (사용자가 로그인할 때와 파일 및 디렉토리를 생성할 때 부여되는 기본 그룹)
- Secondary Groups : 없거나 여러개 존재 (사용자가 파일 또는 디렉토리를 읽거나 쓰거나 실행할 때 지정된 그룹들의 권한을 부여받음)



<br><br><br>
<br><br><br>

## Tomcat

### 파일생성 실패 (Read-only file system)

tomcat을 구동하여 Application을 통해 파일을 생성하고자 할 때, 파일 생성 경로에 적합한 권한*을 부여해도 'Read-only file system' 이슈가 발생하여 파일 생성에 실패하는 경우가 발생할 수 있다.
\* 생성 대상 디렉토리의 사용권한, 소유자, 그룹을 755 & tomcat.tomcat으로 설정

이를 해결하기 위해서, 실행 중인 tomcat process의 pid를 확인한 뒤 프로세스의 mountinfo로 전달된 namespace 중 
파일의 생성위치에 해당하는 파일시스템이 rw인지 확인하고 ro면 해당 위치를 ReadWritePaths 속성으로 등록한 후 시스템 데몬을 re-load한 뒤 톰캣을 재시작한다.


■ 파일 시스템 확인

$ ps -ef | grep tomcat

$ (sudo) vi /proc/${pid}/mountinfo 

    ex) vi /proc/945/mountinfo



■ ReadWritePaths 속성 등록

$ sudo vi /etc/systemd/system/multi-user.target.wants/tomcat9.service

 

- [Service] 하단에 ReadWritePaths 속성을 추가해준다.
ReadWritePaths=${파일을 생성하고자하는 경로}

ex) ReadWritePaths=/example/docuraydata

 

- 시스템 데몬 리로드 후 서비스 재시작

$ systemctl daemon-reload 

$ service tomcat9 restart

 
이후 추가한 경로가 /proc/${pid}/mountinfo 에서 rw로 받아지며 웹 어플리케이션에서 정상적으로 처리된다.


[참고]
해당 이슈는 런타임 프로세스가 시스템에 대해서 처리할 수 있는 오퍼레이션이 제한됨에 따라 발생한다.
(Sandboxing). 일반적인 설정 (/home/docuraydata)일 경우 별도의 설정 없이 파일의 생성이 가능하나 다른 경로를 설정할 경우 위의 path 추가가 필요하다. (/home 경로가 rw로 등록됨에 따라 /home 하위 경로는 sandboxing 처리되지 않는다.)



<br><br><br>
<br><br><br>
<br><br><br>


<br><br><br>

## 프로그램 설치

1. 소스파일 컴파일 설치 - 매우 불편. '2. 패키지 파일 설치방법' 고안됨

2. 패키지 파일 설치
   > $ dpkg

3. 자동 설치 도구 이용 - 수동으로 하던 패키지의 다운로드 ~ 설치 과정을 자동으로 처리
   > $ apt-get install [패키지 이름]    ||   apt-get install [패키지 이름]

APT - Advanced Packagaging Tool



<br><br><br>

## 파일(디렉토리) 이동 / 이름변경 / 복사 / 생성

* mv : 파일을 다른 디렉토리로 이동하거나 다른 이름으로 바꾸고자할 때 사용
> $ mv [-옵션] '원본 디렉토리' '옮길 디렉토리' <br>


_*_ 경로가 동일하면 rename이 되고 다르면 경로가 다르면 파일이 이동 <br>
_*_ rename 명령어 존재

<br>

* cp : 파일 및 디렉토리를 복사
> $ cp [-옵션] '원본 디렉토리' '옮길 디렉토리'


* rsync(Remote sync) : **원격** 또는 **로컬**간에 파일이나 디렉토리를 복사
  - 속도 개선 : 동일 장비 내에서 사용 시 z 옵션을 제거하면 파일을 복사하는데 큰 속도단축을 확인할 수 있음. (z 옵션은 network traffic을 줄이기 위해 사용)



* touch : 파일의 날짜와 시간을 수정하는 명령어 / 0바이트 파일을 생성하기 위해 자주 사용




<br><br><br>


## 파일 다운로드

wget : 비대화식 네트워크 다운로더 (Web GET)
> $ wget [-옵션] URL

ex) wget http://mirror.navercorp.com/apache/tomcat/tomcat-9/v9.0.29/bin/apache-tomcat-9.0.29.tar.gz
> $ tar -xzvf apache-tomcat-9.0.29.tar.gz

tar : 파일의 압축 / 해제 명령어
> $ tar [-옵션] 파일이름

여러 개의 파일을 하나의 파일로 묶거나 풀 때 사용하며 테이프 아카이버(Tape ARchiver)의 앞글자들을 조합하여 tar라 명명



<br><br><br>

## 파일/디렉토리 용량

du(disk usage) : 파일 용량 확인 명령어 (디렉토리의 경우 하위 파일 탐색)
> $ du [-옵션] [File] ... <br>
> $ du -hs ~/shell/



apt install upgrade 꼬였을 때  : ex- invoke-rc.d: could not determine current runlevel

/etc/init.d 쪽과 연관성 존재 (docker 사용시)

https://github.com/microsoft/WSL/issues/1761




<br><br><br>
<br><br><br>

## 모니터링

smartmontools 패키지
- 드라이브 내부 시스템을 활용해서 드라이브 상태를 모니터링 할 수 있는 기능 제공





<br><br><br>
<br><br><br>

### [참고] <br>

  *-* ubuntu apt package dependency tree [offical] - https://packages.ubuntu.com/focal/nginx-extras <br>
  *-* 리눅스 파일시스템 게층 구조 (디렉토리 구조 이해) [공식표준문서] - https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html#purpose5 <br>


  * 리눅스 설치
  *-* vmware 네트워크 모드 (NAT, Bridge, Host Only) - https://tristan91.tistory.com/238 <br>
  *-* VMwared Network setting (port forwarding - NAT) - https://hwan1001.tistory.com/63 <br>

  *-* VMware 리눅스 설치 - https://lindarex.github.io/ubuntu/ubuntu-1804-installation/ <br>
  *-* 'virtual disk as a single file' vs 'Split virtual disk into multiple files' - https://junyharang.tistory.com/8 <br>
  *-* What is LVM > dynamic partitions - https://github.com/johngrib/simple_vim_guide/blob/master/md/vimrc.md <br>

  *-* 파일시스템 & 디스크 파티셔닝 - https://ttps2line.tistory.com/33 <br>
  *-* 파일시스템 확인방법 - https://websetnet.net/ko/commands-to-check-filesystem-in-linux-ubuntu/ <br>

  *-* 리눅스 cpu, memory spec 정보 확인하는 법(Blog) - https://juni5184.tistory.com/19 <br>

<br>

  * SSH
  *-* SSH and OpenSSH - https://www.quora.com/What-are-the-differences-between-SSH-and-OpenSSH-What-are-their-similarities <br>
  *-* Package: SSH [Official] - https://packages.ubuntu.com/bionic/ssh <br>
  *-* Package: OpenSSH [Official] - https://packages.ubuntu.com/bionic/openssh-server <br>
  
  *-* install tomcat in VMware - https://antdev.tistory.com/52 <br>

<br>

  * 방화벽 (firewall)
  *-* ufw 설명 및 사용방법 - https://imcr.tistory.com/11 <br>

<br>

  * 프로세스
  *-* 백그라운드 실행 nohup - https://morningame.tistory.com/154 <br>
  *-* nohup 환경변수 설정 - https://unix.stackexchange.com/questions/308370/how-can-i-set-environment-variables-for-a-program-executed-using-nohup <br>
  *-* 프로세스 종료 (kill 명령어) - https://veneas.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%EC%8B%9C%EA%B7%B8%EB%84%90-%EB%AA%85%EB%A0%B9%EC%96%B4%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EC%A2%85%EB%A3%8C-kill <br>
  

<br>

  * 데이터 편집 (vi/m, awk, sed) <br>
  *-* awk 설명 - https://reakwon.tistory.com/163 <br>
  *-* sed 줄바꿔 데이터 넣는 방법 - https://unix.stackexchange.com/questions/121161/how-to-insert-text-after-a-certain-string-in-a-file <br>
  *-* sed space 문자 표시방법 - https://stackoverflow.com/questions/18439528/sed-insert-line-with-spaces-to-a-specific-line <br>

  *-* vi / vim 단축키 - https://iamfreeman.tistory.com/entry/vi-vim-%ED%8E%B8%EC%A7%91%EA%B8%B0-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC-%EB%8B%A8%EC%B6%95%ED%82%A4-%EB%AA%A8%EC%9D%8C-%EB%AA%A9%EB%A1%9D <br>
  
  *-* 다중 명령어[@@@] - https://jhnyang.tistory.com/66 <br>
  *-* linux background 실행 명령어 (cf. nohup) - https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=lge920904&logNo=220687339025 <br>


  *-* 시스템 (c.f. 서비스 등록) - https://etloveguitar.tistory.com/57 <br>

  *-* ll, ls-l - https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ll,_ls_-l <br>
  *-* 파일 정보 확인 (ls -al) - https://www.leafcats.com/137 <br>
  
  *-* 디렉토리에 있는 디렉토리 / 파일 갯수 확인 - https://blog.leocat.kr/notes/2017/07/27/shell-count-folders-and-files <br>

  *-* grep 명령어 메타문자 - https://zzsza.github.io/development/2017/12/16/linux-4/ <br>
  *-* grep 대시(-) 문자 검색방법 : 더블대시 [stackoverflow] - https://stackoverflow.com/questions/2427913/how-can-i-grep-for-a-string-that-begins-with-a-dash-hyphen <br>
  *-* grep 정규표현식 (RegEx) - https://linuxize.com/post/regular-expressions-in-grep/ <br>
  *-* wc(word count) command - http://www.incodom.kr/Linux/%EA%B8%B0%EB%B3%B8%EB%AA%85%EB%A0%B9%EC%96%B4/wc <br>
  
  <br>

  *-* if 문 대괄호 더블괄호 차이점 - http://bahndal.egloos.com/531206 <br>

  <br>
  
  * 사용자 관리 <br>
  *-* root 계정 ssh 원격 접속 권한 설정 방법 - https://nov19.tistory.com/95 <br>
  *-* 우분투에서 사용자 추가하기 - https://mungiyo.tistory.com/14 <br>
  *-* 계정의 그룹 변경 - https://syuda.tistory.com/159 <br>
  *-* sudo 그룹에 사용자 추가하기 - https://jjeongil.tistory.com/1680 <br>

  <br>

  * 권한 관리 <br>

  *-* 파일 허가권 소유자 및 그룹 - https://darrengwon.tistory.com/853 <br>
  *-* 사용자 관리 - https://withcoding.com/101 <br>
  *-* 그룹 생성 및 권한 부여 - https://twowinsh87.github.io/etc/2018/08/12/etc-iknowledge-linux-group_permission/ <br>
  
  *-* 파일 이동, 이름변경 - https://shinboard.net/archives/4109 <br>
  
  *-* 권한 개념 및 변경 방법 - https://conory.com/blog/19194 <br>
  *-* 권한 및 소유권 변경방법 - https://withcoding.com/103 <br>
  *-* 소유자 및 그룹 관리방법 - https://www.manualfactory.net/13414 <br>

  *-* 사용자 생성 및 그룹 지정 - https://m.blog.naver.com/wideeyed/221512008307 <br>
  *-* [stackExchange] gpasswd vs usermod - https://askubuntu.com/questions/1366061/when-gpasswd-vs-usermod-deluser <br>
  *-* 루트 사용자(root) 권한 사용 명령어 [su / sudo]의 차이점 - https://juni5184.tistory.com/19 <br>
  

  <br>

  * 다운로드
  *-* apt, rpm, wget 방식 차이 (yum 또한 centos 게열) - https://m.blog.naver.com/zozokjs/221212381840 <br>
  *-* 리눅스 프로그램(패키지) 설치 - https://conory.com/blog/42585 <br>
  *-* apt와 apt-get 차이점 - https://ksbgenius.github.io/linux/2021/01/13/apt-apt-get-difference.html <br>
  *-* 파일 다운로드(wget) - https://hippogrammer.tistory.com/158 <br>
  *-* tar 커맨드 개념 - https://recipes4dev.tistory.com/146 <br>
  *-* add-apt-repository를 사용할 수 없을 때... [StackOverflow] - https://askubuntu.com/questions/445536/unable-to-locate-package-add-apt-repository-error <br>

  * 폴더/파일 관리 <br>
  *-* rsync 명령어 사용법 - https://twpower.github.io/153-copy-file-or-directory-using-rsync-command <br>
  *-* rsync 속도 개선을 위한 옵션 설정 (how to speed up rsync) - https://superuser.com/questions/109780/how-to-speed-up-rsync <br>

  <br>

  * 로그
  *-* logrotate와 copytruncate 옵션 - https://brunch.co.kr/@alden/27 <br>
  *-* logrotate 설정방법 - https://www.manualfactory.net/10547 <br>
  *-* logrotate 설정 옵션 - https://suminstory.tistory.com/142 <br>
  *-* logrotate 구조 - https://blog.o3g.org/server/logrotate%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%98%EC%97%AC-%EB%A1%9C%EA%B7%B8-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0/ <br>

  *-* ubuntu에 powershell 설치하는 방법 - https://docs.microsoft.com/ko-kr/powershell/scripting/install/install-ubuntu?view=powershell-7.2 <br>