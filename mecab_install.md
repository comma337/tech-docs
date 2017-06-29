# MeCab
- http://taku910.github.io/mecab/
- 오픈 소스 형태소 분석엔진 중 하나
- 한국어 분석 사전을 이용하여 한국어 형태소 분석 가능
<!--- KoNLPy라는 자연어 처리 패키지도 있는 듯, KoNLPy에서는 여러 형태소 분석기를 포함하여 ?-->

### install
- ubuntu
- mecab 설치
    ```
    sudo apt-get install libmecab-dev
    sudo apt-get install mecab mecab-ipadic-utf8
    ```
- 한국어 사전 파일 설치
    - download : https://bitbucket.org/eunjeon/mecab-ko-dic/downloads/
    ```
    wget https://bitbucket.org/eunjeon/mecab-ko-dic/downloads/mecab-ko-dic-2.0.1-20150920.tar.gz --no-check-certificate
    tar xzvf mecab-ko-dic-2.0.1-20150920.tar.gz
    cd mecab-ko-dic-2.0.1-20150920
    ./configure
    make
    make check
    su -
    cd /home/vagrant/mecab-ko-dic-2.0.1-20150920
    make install
    ```
- 한국어 사전 default 설정
    ```
    vi /etc/mecabrc
    dicdir = /usr/lib/mecab/dic/mecab-ko-dic
    ```
- 설치 확인
    ```
    mecab -d /usr/lib/mecab/dic/mecab-ko-dic(enter)
    테스트 문장 입력(enter)
    ```
- mecab python binder 설치
    - linux(ubuntu)
        ```
        sudo apt-get install g++
        sudo apt-get install python3-dev
        pip3 install mecab-python3
        ```
    - mecab-0.996-ko-0.9.2 설치 error case
        - 출처: http://searchtool.tistory.com/3
        ```
        # 아래와 같은 에러 문구가 나올 경우
        mecab: error while loading shared libraries: l
        ibmecab.so.2: cannot open shared object file: No such file or directory
        
        #step1 su 권한으로 아래의 명령어 입력 입력
        vi /etc/ld.so.conf
        
        # step2 아래 경로 추가 후 저장
        /usr/local/lib
        
        # step3 경로 확인
        ldconfig
        ldconfig -p | grep libmecab
        
        # step 4 아래와 같이 정상적으로 메세지 출력 되는지 확인
        libmecab.so.2 (libc6,x86-64) =&gt; /usr/local/lib/libmecab.so.2
        libmecab.so (libc6,x86-64) =&gt; /usr/local/lib/libmecab.so
        ```
