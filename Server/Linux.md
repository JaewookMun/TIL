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


## 사용자 관리



## 그룹 관리

## 파일 관리

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
  *-* 파일 허가권 소유자 그룹 - https://darrengwon.tistory.com/853 <br>
  *-* 사용자 관리 - https://withcoding.com/101 <br>
  *-* 그룹 생성 및 권한 부여 - https://twowinsh87.github.io/etc/2018/08/12/etc-iknowledge-linux-group_permission/ <br>
  
  *-* 파일 이동, 이름변경 - https://shinboard.net/archives/4109 <br>

  *-* 리눅스 프로그램(패키지) 설치 - https://conory.com/blog/42585 <br>
  *-* apt와 apt-get 차이점 - https://ksbgenius.github.io/linux/2021/01/13/apt-apt-get-difference.html <br>
  *-* 파일 다운로드(wget) - https://hippogrammer.tistory.com/158 <br>
  *-* tar 커맨드 개념 - https://recipes4dev.tistory.com/146 <br>



