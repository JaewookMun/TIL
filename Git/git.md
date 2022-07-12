# Git


## SSL 인증서 확인 제외

git 설정파일
* /etc/gitconfig : --system
* ~/.gitconfig, ~/.config/git/config : --global
* .git/config : --local

global
* git config --global http.sslVerify false





### [참고] <br>
  
  *-* git clone 시 ssl 인증서 오류 해결 - https://late90.tistory.com/461 <br>
  *-* git 사용자 스코프별 설정파일과 옵션 - https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95 <br>