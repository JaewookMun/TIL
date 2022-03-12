# Linux

<br>

## 프로세스
--

Systemd

* init 프로세스에서 개선된 프로세스
* pid1
* 시스템 전반에 영향을 끼침
* linux가 부팅되는 과정에서 시스템을 초기화하고 환경설정을 해주는 역할


c.f.) systemctl

<br><br>

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


<br><br>

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



## 그룹 관리



<br><br>

## 폴더 / 파일 관리




<br><br>

<br><br>


## 프로그램 설치

1. 소스파일 컴파일 설치 - 매우 불편. '2. 패키지 파일 설치방법' 고안됨
2. 패키지 파일 설치
   > $ dpkg
3. 자동 설치 도구 이용 - 수동으로 하던 패키지의 다운로드 ~ 설치 과정을 자동으로 처리
   > $ apt-get install [패키지 이름]    ||   apt-get install [패키지 이름]

APT - Advanced Packagaging Tool

## 파일(디렉토리) 이동 / 이름변경 / 복사

* mv : 파일을 다른 디렉토리로 이동하거나 다른 이름으로 바꾸고자할 때 사용
> $ mv [-옵션] '원본 디렉토리' '옮길 디렉토리' <br>


_*_ 경로가 동일하면 rename이 되고 다르면 경로가 다르면 파일이 이동 <br>
_*_ rename 명령어 존재

<br>

* cp : 파일 및 디렉토리를 복사
> $ cp [-옵션] '원본 디렉토리' '옮길 디렉토리'


<br><br>

## 파일 다운로드

wget : 비대화식 네트워크 다운로더 (Web GET)
> $ wget [-옵션] URL

tar : 파일의 압축 / 해제 명령어
> $ tar [-옵션] 파일이름

여러 개의 파일을 하나의 파일로 묶거나 풀 때 사용하며 테이프 아카이버(Tape ARchiver)의 앞글자들을 조합하여 tar라 명명




<br><br>
<br><br>

### [참고] <br>
  *-* vi / vim 단축키 - https://iamfreeman.tistory.com/entry/vi-vim-%ED%8E%B8%EC%A7%91%EA%B8%B0-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC-%EB%8B%A8%EC%B6%95%ED%82%A4-%EB%AA%A8%EC%9D%8C-%EB%AA%A9%EB%A1%9D <br>
  
  *-* 시스템 (c.f. 서비스 등록) - https://etloveguitar.tistory.com/57 <br>

  *-* ll, ls-l - https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ll,_ls_-l <br>
  *-* 파일 정보 확인 (ls -al) - https://www.leafcats.com/137 <br>
  
  
  <br><br>

  * 권한 관리

  *-* 파일 허가권 소유자 및 그룹 - https://darrengwon.tistory.com/853 <br>
  *-* 사용자 관리 - https://withcoding.com/101 <br>
  *-* 그룹 생성 및 권한 부여 - https://twowinsh87.github.io/etc/2018/08/12/etc-iknowledge-linux-group_permission/ <br>
  
  *-* 파일 이동, 이름변경 - https://shinboard.net/archives/4109 <br>
  
  *-* 권한 개념 및 변경 방법 - https://conory.com/blog/19194 <br>
  *-* 권한 및 소유권 변경방법 - https://withcoding.com/103 <br>
  *-* 소유자 및 그룹 관리방법 - https://www.manualfactory.net/13414 <br>

  <br>

  *-* 리눅스 프로그램(패키지) 설치 - https://conory.com/blog/42585 <br>
  *-* apt와 apt-get 차이점 - https://ksbgenius.github.io/linux/2021/01/13/apt-apt-get-difference.html <br>
  *-* 파일 다운로드(wget) - https://hippogrammer.tistory.com/158 <br>
  *-* tar 커맨드 개념 - https://recipes4dev.tistory.com/146 <br>



