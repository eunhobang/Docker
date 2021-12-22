## 설명
- 도커 설치 하고 컨테이너 생성이 안 돼서 처음부터 다시 설치하기 위해서 도커 삭제
- 삭제 명령어 통하지 않을 때
- "docker -v" 명령어로 도커가 삭제가 된 것을 확인할 수 있음


```console
root@DESKTOP-JM4UFFA:~# sudo apt-get remove docker*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'docker-engine-cs' for glob 'docker*'
Note, selecting 'docker-compose' for glob 'docker*'
Note, selecting 'docker-ce-rootless-extras' for glob 'docker*'
Note, selecting 'docker' for glob 'docker*'
Note, selecting 'docker.io-doc' for glob 'docker*'
Note, selecting 'docker2aci' for glob 'docker*'
Note, selecting 'docker-engine' for glob 'docker*'
Note, selecting 'docker-registry' for glob 'docker*'
Note, selecting 'docker-scan-plugin' for glob 'docker*'
Note, selecting 'docker-doc' for glob 'docker*'
Note, selecting 'docker-ce' for glob 'docker*'
Note, selecting 'docker-ce-cli' for glob 'docker*'
Note, selecting 'docker.io' for glob 'docker*'
Note, selecting 'docker-doc' instead of 'docker.io-doc'
Package 'docker-engine' is not installed, so not removed
Package 'docker-engine-cs' is not installed, so not removed
Package 'docker' is not installed, so not removed
Package 'docker-compose' is not installed, so not removed
Package 'docker-registry' is not installed, so not removed
Package 'docker2aci' is not installed, so not removed
Package 'docker-doc' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
Package 'docker-ce-rootless-extras' is not installed, so not removed
The following packages will be REMOVED:
  docker-ce docker-ce-cli docker-scan-plugin
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 278 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 166486 files and directories currently installed.)
Removing docker-ce (5:20.10.12~3-0~ubuntu-focal) ...
Removing docker-ce-cli (5:20.10.12~3-0~ubuntu-focal) ...
Removing docker-scan-plugin (0.12.0~ubuntu-focal) ...
Processing triggers for man-db (2.9.1-1) ...
root@DESKTOP-JM4UFFA:~# docker -v
-bash: /usr/bin/docker: No such file or directory
```
