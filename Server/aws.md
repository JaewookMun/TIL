# AWS

<br>

### S3 (Amazon Simple Storage Service)

<br>

**AWS CLI 이슈**

ubuntu 서버 터미널 화면에서 직접 명령어를 날렸을 때는 정상 실행되나 크론(Cron)을 활용하여 스크립트 파일의 수행을 설정 했을 때 정상적으로 실행되지 않는 경우가 존재한다. (credential 문제)

AWS CLI는 cli 사용 시 '~/.aws/config' 또는 '~/.aws/credentials' 파일을 찾는다.

만약 $HOME의 경로가 '/'라면 client는 위 두 파일을 찾지 못하기 때문에, <br>
script 내에 적절한 $HOME 경로를 설정하면 cron으로 스크립트를 실행시켜도 문제없이 동작한다.



<br><br><br>

### [참고] <br>
  * aws cli examples <br>
  *-* aws cli usage with bash - https://docs.aws.amazon.com/ko_kr/code-library/latest/ug/bash_2_s3_code_examples.html <br>
  *-* Can't run AWS CLI from CRON (credentials) [StackExchange] - https://serverfault.com/questions/614890/cant-run-aws-cli-from-cron-credentials<br>
  *-* related above - https://serverfault.com/questions/614890/cant-run-aws-cli-from-cron-credentials<br>  
  *-* aws cli not working - https://stackoverflow.com/questions/26480860/aws-not-working-working-from-cronjob/26480929#26480929<br>
    
  
  <br><br>

  * concept and tips <br>

  *-* aws cli 오류 해결하는 법 (official) - https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/cli-chap-troubleshooting.html <br>
  *-* AWS S3 활용 및 단점 분석 (blog) - https://devocean.sk.com/blog/techBoardDetail.do?ID=163606 <br>