---
title: tar
icon: material/bash
---

보통 리눅스에서 파일을 압축 파일을 다룰 때, "tar로 압축(compress)한다"는 표현을 쓰는 경우가 많은데,  
정확히 말하자면 tar 자체는 "데이터의 크기를 줄이기 위한 파일 압축"을 수행하지 않는다.  
단지 여러 파일을 하나의 파일로 묶는 용도로 사용될 뿐이다.  
대신, tar를 통해 하나로 합쳐진 파일을 gzip 또는 bzip2 방식을 사용하여 압축할 수 있다.  
tar가 널리 쓰이게 된 이유 중 한 가지는, 단순 아카이버 기능에 더해, tar로 묶여지기 전  
파일들의 속성과 심볼릭 링크, 디렉토리 구조 등을 그대로 가져갈 수 있는 특징 때문이다.  
그래서 최근에는 리눅스 용 프로그램, 데이터, 소스 및 라이브러리 등을 배포하는 용도로 많이 사용된다. 

---

### 1. 압축하기
  * `-c` : compress, tar 아카이브 생성 (기존 아카이브 덮어쓰기)
  * `-v` : 처리되는 과정을 나열
  * `-f` : 대상 tar 아카이브 지정 (기본 옵션)

    > tar압축

    ``` bash
    $ tar -cvf [파일명.tar] [폴더명]
    ```
    ``` bash
    $ tar -cvf test.tar test_folder
    ```

    > tar.gz 압축

    ``` bash
    $ tar -zcvf [파일명.tar.gz] [폴더명]
    ```
    ``` bash
    $ tar -zcvf test.tar.gz test_folder
    ```

    > zip 압축

    ``` bash
    $ zip [파일명.zip] [폴더명]
    ```
    ``` bash title="현재 폴더의 전체를 압축"
    $ zip test.zip ./*
    ```
    ``` bash title="현재 폴더의 모든 것과 현재 폴더의 하위 폴더들까지 모두 압축"
    $ zip test.zip -r ./*
    ```

### 2. 압축 해제 하기
  * `-x` : extract, tar 아카이브에서 파일 추출 
  * `-v` : 처리 되는 과정을 나열
  * `-f` : 대상 tar 아카이브 지정 (기본 옵션)

    > tar 압축 해제

    ``` bash
    $ tar -xvf [파일명.tar]
    ```

    > tar.gz 압축 해제

    ``` bash
    $ tar -zxvf [파일명.tar.gz]
    ```
    ``` bash
    $ tar -zxvf test.tar.gz
    ```

    > zip 압축 해제

    ``` bash
    $ unzip [파일명.zip]
    ```
    ``` bash
    $ unzip test.zip
    ```
    ``` bash title="특정 폴더에 압축 해제"
    $ unzip test.zip -d ./target_folder
    ```