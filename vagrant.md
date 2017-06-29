## Vagrant란
- vitual machine 관리 툴, 가상머신을 생성(init)/시작(up)/중지(suspend)/재개(resume)/종료(halt)/삭제(destroy)/배포(push) 등 가능
- Vagrantfile 설정으로 자동 provisioning 가능, host pc와 포트 포워딩/폴더 공유 등 가능
- vs Docker : docker는 (OS를 제외한)container 관리, vagrant는 vm 관리

## 설치
- VMWare
  Vitual Box 등 https://www.virtualbox.org/wiki/Downloads
  Vagrant에서 box 생성 시 자동 설치도 가능하나 먼저 설치하여 VM Image 생성 위치 등 지정함
- Vagrant https://www.vagrantup.com/downloads.html
- 설치 확인 : vagrant 명령어 실행 시 사용법 안내 표시


## 명령어
### vagrant init <box name/option>
- VM 이미지 생성하기 위한 Vagrantfile(및 .vagrant 폴더)이 생성됨
  명령어를 실행하고 있는 폴더 내 1개의 Vagrantfile 존재하며 Multi VM 생성 가능. 여러 VM들을 동시에 사용하지 않으려면 폴더로 분리
- 기본 설정으로는 1개의 vm만 생성됨(id: vagrant/ pw:vagrant)


### vagrant box add <base box name> <base box url/option>
- base box : VM Image 생성 시 참조할 template, base image
- base box list : http://www.vagrantbox.es/
- Vagrantfile 파일에 config.vm.box 값을 설정해놓은 경우 base box를 미리 추가(box add)하지 않아도 vagrant up 할때 다운로드 된다고 하는데 윈도우에서 인증서 문제 발생 시 자동 다운로드 되지 않고 못찾는다는 메세지만 표시됨. 
  --insecure 옵션을 사용하여 박스 추가 후 실행 가능

### vagrant box list
- 설치된 box 조회

### vagrant up
- VM booting. VM 환경 실행 및 VM 내부 OS 부팅
- VM image가 없는 경우 실제 생성됨

### vagrant suspend
- 현재 상태를 저장하고 중지. 메모리 해제 되지 않고 VM OS 중지되지 않음

### vagrant resume
- suspend된 VM 재실행

### vagrant halt
- VM shutdown. 메모리 해제/ VM OS 종료

### vagrant destroy
- VM image 삭제

### vagrant status
- VM 상태 보기

### vagrant ssh
- ssh 접속..이긴 한데 windows prompt용 프로그램이 마땅한게 없음. putty 사용하여 접속 가능

### vagrant reload
- 재시작

### vagrant package --base <vm name> --output <box name>
- VM Image를 box로 생성

## Vagrantfile
- Vagrantfile을 생성하여 auto provisioning 가능
- 설정 예
  ```
  # -*- mode: ruby -*-
  # vi: set ft=ruby :

  Vagrant.configure("2") do |config|
    # base box
    config.vm.box = "ubuntu/trusty64"
    config.vm.box_download_ca_cert = "../keys/cert.pem"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
    end
    config.vm.boot_timeout = 30
    config.vm.network "forwarded_port", guest: 80, host: 80, host_ip: "127.0.0.1"
    config.vm.synced_folder "D:/vm/keys", "/home/vagrant/keys"
  end
  ```

- Directory Mount
  - vm 내에서 공유 디렉토리가 마운트 되지 않는 경우 명령어로 마운트 시킬 수 있다.
    - home_vagrant_data : vm의 공유 폴더로 설정되어 있는 머신 폴더 이름
    - /home/vagrant/data : vm 내 경로
    ```
    sudo mount -t vboxsf home_vagrant_data /home/vagrant/data
    ```


<!--
-o uid=1000,gid=1000

, type: "nfs", :nfs => true, :mount_options => ['nolock,vers=3,udp']
추가

vm내 sw 버전 관리 등
: chef, puppet... 등 사용
서버 없으면 chef_solo도 있다
config.vm.provision 

<!--