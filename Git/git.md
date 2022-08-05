# Git

## Git bash 사용자 정보

* 확인
git config user.name
git config user.email

* 변경
git config --global user.name ${name}
git config --global user.email ${email}



<br><br><br>

## SSL 인증서 확인 제외

git 설정파일
* /etc/gitconfig : --system
* ~/.gitconfig, ~/.config/git/config : --global
* .git/config : --local

global
* git config --global http.sslVerify false



<br><br><br>

## git stash

git pull을 통해 작업 내용을 받기 전에 현재 변경 중인 작업을 임시로 저장하는 기능

1. git stash
2. git pull
3. git stash pop



## 원격 저장소 만들기




### [참고] <br>
  
  * config - 사용자 정보 <br>
  *-* bash user정보 확인/변경 - https://somjang.tistory.com/entry/Git-Git-Bash-%ED%84%B0%EB%AF%B8%EB%84%90-%EA%B3%84%EC%A0%95-%EB%B3%80%EA%B2%BD-%EB%B0%A9%EB%B2%95 <br>
  *-* git clone 시 ssl 인증서 오류 해결 - https://late90.tistory.com/461 <br>
  *-* git 사용자 스코프별 설정파일과 옵션 - https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95 <br>
  *-* git config 설정 및 조회 방법 [@@@@@] - https://www.geeksforgeeks.org/how-to-set-git-username-and-password-in-gitbash/?ref=leftbar-rightbar <br>

  <br>

  * repository 관리 <br>
  *-* git stash란 ? 개념설명 블로그 - https://gmlwjd9405.github.io/2018/05/18/git-stash.html <br>

  <br>

  * 원격 저장소 - Remote Repository <br>
  *-* Git 서버, 서버에 Git 설치 [official] - https://git-scm.com/book/ko/v2/Git-%EC%84%9C%EB%B2%84-%EC%84%9C%EB%B2%84%EC%97%90-Git-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0#_getting_git_on_a_server <br>
  *-* 원격저장소 만드는 방법 (1) - https://hoodiejun.tistory.com/15 <br>
  *-* 원격저장소 만드는 방법 (2) - https://velog.io/@kimjjs100/%EB%82%98%EB%A7%8C%EC%9D%98-git-%EC%84%9C%EB%B2%84-%EB%A7%8C%EB%93%A4%EA%B8%B0-3-%EC%9B%90%EA%B2%A9%EC%A0%80%EC%9E%A5%EC%86%8C-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0 <br>
  *-* 원격저장소 만드는 방법 (가장 심플) - http://egloos.zum.com/devxpert/v/1034173 <br>
  