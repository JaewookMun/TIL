# 도커(docker)
---

도커는 컨테이너 기반의 오픈소스 가상화 플랫폼을 의미한다.

다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순하게 해준다.


<br><br><br>

## Docker Desktop vs Docker Engine

여러가지 차이점이 존재하지만 Docker Desktop은 Window, Mac 용이며 Docker Desktop을 설치하면 Virtual Machine이 추가로 설치된다고 간단히 정리
(Docker Desktop이 좀더 포괄적 개념이라고 생각할 수 있음.)


<br><br><br>
<br><br><br>

## 설치

**Recommended Process**
0. Uninstall old versions <br>
1. Set-up the repository : update and install packages
   sudo apt-get update
   sudo apt-get install ca-certificates curl gnupg lsb-release

   sudo mkdir -p /etc/apt/keyrings
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

   echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

2. Install Docker Engine : update packages and install the latest version of Docker Engine
   sudo apt-get update
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

   * for specific version, install docker after selecting version

3. verify Docker Engine is installed
   sudo docker run hello-world
   

<br><br><br>

Install using the convenience script
* script installation은 production environment 에는 권장되지 않음.

curl -fsSL https://get.docker.com -o get-docker.sh <br>
(DRY_RUN=1) sh ./get-docker.sh


<br><br><br>

## Post-Installation

Don't use sudo keyword > non-root user
i. sudo groupadd docker <br>
ii. sudo usermod -aG docker $USER <br>
iii. newgrp docker <br>



<br><br><br>

## Using Docker

Q - Docker: Having issues installing apt-utils
https://stackoverflow.com/questions/51023312/docker-having-issues-installing-apt-utils

<br>

cf. postgresql - https://stackoverflow.com/questions/42653690/psql-could-not-connect-to-server-no-such-file-or-directory-5432-error


<br><br><br>

## Dockfile

ENV vs ARG
 - ARG : build 시점에 사용
 - ENV : 환경변수 지정



<br><br><br>
<br><br><br>
<br><br><br>

### [참고] <br>
  *-* 도커란? 기본적인 설명 - https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html <br>
  *-* 도커 설명 - https://cultivo-hy.github.io/docker/image/usage/2019/03/14/Docker%EC%A0%95%EB%A6%AC/ <br>
  *-* Docker Desktop vs Docker Engine - https://forums.docker.com/t/difference-between-docker-desktop-and-docker-engine/124612 <br>
  *-* workdir (기본폴더) [official] - https://docs.docker.com/engine/reference/builder/#workdir <br>
  *-* Dockerfile naming convention [official] - https://docs.docker.com/engine/reference/commandline/build/#specify-a-dockerfile--f <br>
  *-* stackoverflow - https://stackoverflow.com/questions/26077543/how-to-name-dockerfiles <br>
  *-* Dockerfile Reference [official] - https://docs.docker.com/engine/reference/builder/ <br>
  *-* ARG (dockerfile 내부) vs ENV (환경변수) : difference - https://stackoverflow.com/questions/41916386/arg-or-env-which-one-to-use-in-this-case <br>


  <br>

  * Installation <br>
  *-* install Docker Engine on Ubuntu - https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository <br>
  *-* how to install Docker on **Ubuntu 16.04** - https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04 <br>
  *-* just use docker without 'sudo' keyword - https://docs.docker.com/engine/install/linux-postinstall/ <br>

  <br>

  * Settings - Dockerfile
  *-* Dockerfile (1) - https://blog.d0ngd0nge.xyz/docker-dockerfile-write/ <br>
  *-* Dockerfile RUN command - https://freedeveloper.tistory.com/187 <br>
  *-* timezone setup [stackExchange] - https://serverfault.com/questions/949991/how-to-install-tzdata-on-a-ubuntu-docker-image <br>
  *-* Dockerfile timezone setup - https://stynxh.github.io/2020-07-26-set-timezone-when-ubuntu-docker-image-build/ <br>
  *-* Dockerfile process를 실행할 사용자 추가 - https://passwd.tistory.com/66 <br>
  *-* 사용자/root 게정 암호 설정 - https://stackoverflow.com/questions/66190675/docker-set-user-password-non-interactively <br>
  *-* 계정 sudo 권한 주기 - https://starseeker711.tistory.com/176 <br>
  *-* Docker container 자동 실행 [Docker.service] - https://help.iwinv.kr/manual/read.html?idx=572 <br>

  <br>

  * Usage <br>
  *-* 기본사용법 (search, pull, create, run) blog -  https://sleepyeyes.tistory.com/67 <br>
  *-* search 옵션 - https://stackoverflow.com/questions/53742359/docker-search-and-description-column <br>
  *-* docker 명령 내리기 - https://eyeballs.tistory.com/49 <br>

  *-* @@@@ docker 내부 통신 [host] (container에서 localhost 사용하기) - https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach <br>
  *-* docker cp 사용시 [getent unable to find entry "" in passwd database] - https://stackoverflow.com/questions/61204958/how-to-change-file-ownership-of-db-backup-in-sql-server-container <br>