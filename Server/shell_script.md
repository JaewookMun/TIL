## Shell Script

* 셸 스크립트
<br>

* **작성방법**
  * 맨 첫줄은 #!/bin/bash 를 작성한다.
``` bash 
#!/bin/bash

# example

REPOSITORY=/home/ec2-user/app/step2
PROJECT_NAME=springboot

cd $REPOSITORY/$PROJECT_NAME/

```
<br>

* **기본 if 문**
  * if [조건] then 수행 명령 fi 구조이며, 'fi'는 if문의 종료를 의미한다.
    c.f. - finished

``` bash
if [조건]
then
  수행할 명령
fi
```

* **if else 문**
  * else를 제외하고 기본 if문과 동일

``` bash
if [조건]
then
  수행할 명령
else
  수행할 명령
fi

```



