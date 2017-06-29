linux command tips

### 네트워크 확인
    ```
    telnet host 24224
    nmap -p 24224 -sU host
    ```


### 사용자 확인
    ```
    cat /etc/passwd             # 전체
    grep /bin/bash /etc/passwd  # /bin/bash 적용된 사용자 목록
    ```
    - /sbin/nologin : shell 권한 없는 경우


### 백그라운드 실행
    ```
    명령어 &
    nohup 명령어 & # session 종료 후에도 유지
    ```

### symbolic link
    ```
    ln -s 실제경로 생성경로
    ```

### 파일 나누기
    ```
    split -b 100m file_name # 용량별
    split -l 1000 file_name # 라인별
    split -l 1000 file_name prefix_ # 접두사 붙이기
    ```

### file byte 단위 변경 조회
    ```
    ls -l --block-size=m
    ```

### 디스크 용량 확인
    ```
    df <option>
    ```

### OS version
    ```
    cat /etc/issue
    ```

### 폴더 찾기
    ```
    find /usr -name '{name}' -type d
    ```

### apt
- ubuntu package 관리툴
    - apt, aptitude, ...
- 명령어
    - apt-get update
    - apt-get install {package name}
    - apt-get remove {package name}
    - apt-get purge {package name}
        - 설정 파일까지 삭제
    - apt-cache search {package name}

### aptitude
- 명령어
    - aptitude : gui 화면에서 확인 가능

