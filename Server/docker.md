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
<br><br><br>
<br><br><br>

### [참고] <br>
  *-* 도커란? 기본적인 설명 - https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html <br>
  *-* 도커 설명 - https://cultivo-hy.github.io/docker/image/usage/2019/03/14/Docker%EC%A0%95%EB%A6%AC/ <br>
  *-* Docker Desktop vs Docker Engine - https://forums.docker.com/t/difference-between-docker-desktop-and-docker-engine/124612 <br>

  * Installation <br>
  *-* install Docker Engine on Ubuntu - https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository <br>
  *-* how to install Docker on **Ubuntu 16.04** - https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04 <br>
  *-* don't use 'sudo' keyword - https://docs.docker.com/engine/install/linux-postinstall/ <br>

  <br>

  * usage <br>
  *-* 기본사용법 (search, pull, create, run) blog -  https://sleepyeyes.tistory.com/67 <br>
  *-* search 옵션 - https://stackoverflow.com/questions/53742359/docker-search-and-description-column <br>
  *-* docker 명령 내리기 - https://eyeballs.tistory.com/49 <br>

  *-* @@@@ docker 내부 통신 (container에서 localhost 사용하기) - https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach <br>