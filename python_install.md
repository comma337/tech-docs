# Python 개발환경 구축

#### OS
- linux(ubuntu/trusty64 기준)
  : ubuntu에 python2.x, python3.x이 기본 설치되어 있음
  ```
  sudo apt-get install python
  ```
- osx(sierra 기준)
  : python2.x, python3.x(?) 포함
  ```
  brew install python
  ```
- windows 또는 다운로드 설치 시
  : https://www.python.org/downloads/

#### 버전 확인
```
python --version
python3 --version # windows에서 안됨, 추가 설정 필요
```

#### pip 설치
- pip : Python Package 관리툴, python2 2.7.9 또는 python3 3.4 이후에는 포함되어 있음
- get-pip.py 다운로드 > 설치(setuptools 포함)
  https://pip.pypa.io/en/latest/installing/
  ```
  sudo python ./data/get-pip.py
  ```
- osx
  ```
  sudo easy_install pip
  ```

#### 환경 설정으로 --cert 적용
- https://pip.pypa.io/en/stable/reference/pip/?highlight=config
- linux
  ```
  vi ~/.bashrc
  export PIP_CERT=/home/vagrant/data/ssl.pem
  ```
- 인증서 설정해도 안되면 옵션 추가
  ```
  pip install module --trusted-host pypi.python.org
  ```

#### python 가상환경 설정
- virtualenv 설치
  ```
  sudo pip install virtualenv
  ```

- 가상 환경 생성(verion 3.4)
  ```
  virtualenv -p python3.4 venv
  ```
  - windows에서 버전별 예약어 미등록 시 python full path로 호출

- 가상 환경 실행
  - linux, osx
    ```
    source ./venv/bin/activate
    ```
  - windows
    ```
    .\venv\Scripts\activate
    ```
    - powershell에서 스크립트 실행 오류 발생 시 다음 설정 적용
      ```
      Set-ExecutionPolicy RemoteSigned
      ```
  
- 가상 환경 종료
  ```
  deactivate
  ```

#### VS Code에서 virtualenv 사용 설정
- settings.json 추가
```
  "editor.rulers": [80,100],
  "python.pythonPath": "/Users/comma/venv/bin/python3",
  "python.autoComplete.extraPaths": [
      "/Users/comma/venv/bin/python3",
      "/Users/comma/venv/bin/python3/site-packages"
    ]
```

### python setup.py install 로 설치한 파일 삭제
  ```
  python setup.py install --record uninstall.txt
  cat uninstall.txt | xargs rm -rf
  ```