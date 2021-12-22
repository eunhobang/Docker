# Docker

sudo apt-get remove docker-engine docker.io containerd runc

sudo apt-get update
sudo apt-get upgrade

패키지 설치
  sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release

GPG Key 인증
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
<!-- sudo apt-key fingerprint 0EBFCD88 -->

도커 레파지토리 추가(도커 설치를 위한 작업)
<!--   add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" -->
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"

apt docker 설치
  sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io

도커 설치
  sudo apt-get install docker-ce
  *설치를 계속할지를 물어오면 ‘y’를 입력한다.

도커 설치&버전 확인
  docker version
  docker -v
  
시스템 부팅시 docker가 시작되도록 설정하고 실행
  sudo systemctl enable docker && service docker start
  
도커 상태 확인
  sudo systemctl status docker

도커 시작
  sudo systemctl start docker
 
도커 컨테이너 확인
  docker ps
  
Issue
  - Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
  *해당 라인을 읽어보면 unix:///var/run/docker.sock에 있는 docker daemon에 연결할 수 없으므로 docker daemon이 돌고있는지 물어보고 있음
  *즉 docker daemon은 docker.sock에서 돌고 있다는 뜻
  
  

개념
1. dockerd = docker daemon
  - 컨테이너들을 관리하는 백그라운드 프로세스
  - dockerd를 실행하기 위해서 터미널에 dockerd 를 입력하면 됨
2. dockerd와 socker의 관계
  - Docker daemon은 Docker Engine API 요청을 unix, tcp, rd라는 3개 타입의 소켓으로 받을 수 있다.
  - default는 root 권한에 /var/run/docker.sock 에서 생성된 unix 도메인 소켓이다.
  - unix:///var/run/docker.sock은 unix 컴퓨터와 통신을 하기 위한 소켓의 위치를 말함


```console
root@DESKTOP-JM4UFFA:~# sudo apt-get remove docker-engine docker.io containerd runc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'docker-engine' is not installed, so not removed
Package 'containerd' is not installed, so not removed
Package 'runc' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@DESKTOP-JM4UFFA:~# sudo apt-get update
Hit:1 https://download.docker.com/linux/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease
Get:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:6 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [1069 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1400 kB]
Get:8 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [35.7 kB]
Get:9 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [9096 B]
Get:10 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [668 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [277 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.4 kB]
Get:13 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [13.0 kB]
Get:14 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2464 B]
Get:15 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [14.7 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [884 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [363 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [19.9 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:20 http://archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7972 B]
Get:21 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [11.3 kB]
Fetched 5178 kB in 17s (308 kB/s)
Reading package lists... Done
root@DESKTOP-JM4UFFA:~# sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
Reading package lists... Done
Building dependency tree
Reading state information... Done
lsb-release is already the newest version (11.1.0ubuntu2).
lsb-release set to manually installed.
ca-certificates is already the newest version (20210119~20.04.2).
curl is already the newest version (7.68.0-1ubuntu2.7).
gnupg is already the newest version (2.2.19-3ubuntu2.1).
apt-transport-https is already the newest version (2.0.6).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@DESKTOP-JM4UFFA:~# curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
OK
root@DESKTOP-JM4UFFA:~# sudo apt-key fingerprint 0EBFCD88
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]

root@DESKTOP-JM4UFFA:~# add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
Hit:1 https://download.docker.com/linux/ubuntu focal InRelease
Hit:2 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
root@DESKTOP-JM4UFFA:~# sudo apt-get install docker-ce
Reading package lists... Done
Building dependency tree
Reading state information... Done
docker-ce is already the newest version (5:20.10.12~3-0~ubuntu-focal).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@DESKTOP-JM4UFFA:~# docker version
Client: Docker Engine - Community
 Version:           20.10.12
 API version:       1.41
 Go version:        go1.16.12
 Git commit:        e91ed57
 Built:             Mon Dec 13 11:45:33 2021
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
root@DESKTOP-JM4UFFA:~# docker ps
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```
