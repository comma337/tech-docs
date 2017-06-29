# TensorFlow
google에서 만든 머신러닝 라이브러리
- https://www.tensorflow.org/
- https://github.com/tensorflow/tensorflow


## python tensorflow package 설치
  - https://www.tensorflow.org/install/install_linux#InstallingVirtualenv
  - 현재 python3.4를 virtual environment로 사용하고 있어 해당 가상환경 내 설치함
    ```
    # 가상환경 실행
    source ~/venv/bin/activate

    # CPU 버전 설치(GPU 버전 깔려면 NVIDIA® GPU 가 있고 CUDA, cuDNN 등 패키지 설치 필요)
    pip3 install --upgrade tensorflow
    ```


### tensor
- 데이터 구조, 다차원 데이터 배열
- tensor
  | rank | shape | dimension number | math entity | example |
  |:--:| -- |:--:| -- | -- |
  | 0 | [] | 0-D | scalar | s = 483 |
  | 1 | [D0] | 1-D | vector | v = [1.1, 2.2, 3.3] |
  | 2 | [D0, D1] | 2-D | matrix | m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]] |
  | 3 | [D0, D1, D2] | 3-D | 3-tensor | t = [[[2], [4], [6]], [[8], [10], [12]], [[14], [16], [18]]] |






