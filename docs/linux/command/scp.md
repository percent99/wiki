---
title: scp
icon: material/bash
---

**scp**는 **SecureCopy**의 약자로, 원격서버에 있는 파일과 폴더를 전송하거나 가져오기 위해 사용하는 명령어이다. 
**ssh** 원격 접속 프로토콜을 기반으로 하며, ssh와 동일한 22번 포트를 이용하기 때문에 password/identity file을 이용해 안전하게 송수신 할 수 있다.

`local→remote`, `remote→local`, `remote→remote` 로의 송수신이 모두 가능하다.

---

### 사용법

``` bash
$ scp [options] [source] [target]

# source : 파일을 보낼 주소
# target : 파일을 받을 주소
```

1. 로컬에서 원격으로 (Local → Remote)
  ``` bash
  $ scp [전송할 파일 경로] [유저명]@[IP주소]:[받을 경로]

  EX) 로컬의 /home/example.txt 파일을 원격지의 /home/test 디렉토리로 전송
  $ scp /home/example.txt dhj@141.211.xx.xxx:/home/test
  ```

2. 원격에서 로컬로 (Remote → Local)
  ``` bash
  $ scp [유저명]@[IP주소]:[전송할 파일 경로] [받을 경로]

  EX) 원격지의 /home/test.txt 파일을 로컬의 /home/example 디렉토리로 전송
  $ scp dhj@141.211.xx.xxx:/home/test.txt /home/example
  ```

3. 원격에서 원격으로 (Remote → Remote)
  ``` bash
  $ scp [유저명]@[IP주소]:[전송할 파일 경로] [유저명]@[IP주소]:[받을 경로]

  EX) A 원격지의 /home/test.txt 파일을 B 원격지의 /home/example 디렉토리로 전송
  $ scp dhj@141.211.xx.xxx:/home/test.txt gildong@141.223.xx.xxx:/home/example
  ```

### 옵션 (options)

* `-r`: 폴더를 복사할 때 사용(전송 대상을 폴더로 지정). 모든 폴더들을 재귀적으로 복사함.
* `-P`: ssh 포트 지정
* `-i`: identity file을 지정해서 사용(identity file 경로를 지정)
  ``` bash
  $ scp -i ~/.ssh/dhj-server-private ~/example.txt dhj@141.223.xx.xxx:/home/test
  ```
* `-v`: 상세내용을 보면서 디버깅 할 때 사용(verbose 모드)
* `-p`: 전송 시 파일 수정 시간과 권한을 유지
  ``` bash
  $ scp -P 22 dhj@141.223.xx.xxx:/home/dhj/example.txt /home/test
  ```