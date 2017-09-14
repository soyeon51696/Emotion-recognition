## A. "OpenCV 설치하기"


#### 1. 기존 버전 존재 확인
> ~ $ pkg-config --modversion opencv
  - 이 코드를 입력 후 'Package opencv was not found in the pkg-config search path.~~..'와 같은 메세지가 나타난다면 2.진행
  - 이 코드를 입력 후 윗줄과 같은 메세지가 출력되지 않고 버전이 출력된다면 1-1. 진행


##### 1-1. 기존 버전 삭제
> $ sudo apt-get purge libopencv* python-opencv
> $ sudo apt-get autoremove



#### 2. 패키지 업그레이드
> $ sudo apt-get update
> $ sudo apt-get upgrade



#### 3. OpenCV 설치 시 필요한 패키지 설치
> $ sudo apt-get install build-essential cmake

> $ sudo apt-get install pkg-config

> $ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev

> $ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev 

> $ sudo apt-get install libxvidcore-dev libx264-dev libxine2-dev

> $ sudo apt-get install libv4l-dev v4l-utils

> $ sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev 

> $ sudo apt-get install libqt4-dev

> $ sudo apt-get install mesa-utils libgl1-mesa-dri libqt4-opengl-dev 

> $ sudo apt-get install libatlas-base-dev gfortran libeigen3-dev

> $ sudo apt-get install python2.7-dev python3-dev

> $ sudo apt-get install python-numpy python3-numpy



#### 4. OpenCV 설정하기
> ~$ mkdir opencv
> ~$ cd opencv

> ~/opencv$ wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.2.0.zip

> ~/opencv$ unzip opencv.zip

> ~/opencv$ wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.2.0.zip

> ~/opencv$ unzip opencv_contrib.zip

> ~/opencv$ls  -d*/ 
- 실행 시, _opencv-3.2.0/  opencv_contrib-3.2.0/_ 가 뜨면 작업 성공!



### 5. Compile
> ~/opencv$ cd opencv-3.2.0/

> ~/opencv/opencv-3.2.0$ mkdir build

> ~/opencv/opencv-3.2.0$ cd build

> ~/opencv/opencv-3.2.0$ cmake -D CMAKE_BUILD_TYPE=RELEASE \ -D CMAKE_INSTALL_PREFIX=/usr/local \-D WITH_TBB=OFF \
-D WITH_IPP=OFF \-D WITH_1394=OFF \-D BUILD_WITH_DEBUG_INFO=OFF \-D BUILD_DOCS=OFF \
-D INSTALL_C_EXAMPLES=ON \-D INSTALL_PYTHON_EXAMPLES=ON \-D BUILD_EXAMPLES=OFF \-D BUILD_TESTS=OFF \-D BUILD_PERF_TESTS=OFF \-D ENABLE_NEON=ON \-D WITH_QT=ON \-D WITH_OPENGL=ON \-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.2.0/modules \-D WITH_V4L=ON  \-D WITH_FFMPEG=ON \-D WITH_XINE=ON \-D BUILD_NEW_PYTHON_SUPPORT=ON \../

- 실행 후,
_-- Configuring done_
_-- Generating done_
와 같은 메세지가 출력되면 작업 성공 

> ~/opencv/opencv-3.2.0$ cat /proc/cpuinfo | grep processor | wc -l
로 CPU갯수 확인
> ~/opencv/opencv-3.2.0$ time make -j4(글쓴이 CPU갯수는 4개)

> ~/opencv/opencv-3.2.0/build$ sudo make install

> ~/opencv/opencv-3.2.0/build$ cat /etc/ld.so.conf.d/*
실행 시, _/usr/lib/x86_64-linux-gnu/libfakeroot_ 출력되면 성공



#### 6. 설치 확인
> ~/opencv/opencv-3.2.0/build$ pkg-config --modversion opencv
- 실행 시, 설치한 버전(여기선 3.2.0)이 출력되면 설치 성공

## B. "Dlib 설치"
> $ sudo apt-get install build-essential cmake
> $ sudo apt-get install libgtk-3-dev
> $ sudo apt-get install libboost-all-dev

> $ wget https://bootstrap.pypa.io/get-pip.py
> $ sudo python get-pip.py

> $ pip install numpy
> $ pip install scipy
> $ pip install scikit-image

> $ pip install dlib
오류 발생 시,
> $ pip install dlib --user

설치 후,
> $ python
'>>> import dlib'
'>>> import cv2'

오류 없으면 성공!





## C. "Clib 설치"

#### 1. 기존 설치 확인
> rpm -qa | grep gcc
실행 시, rpm이 설치되어있지않다고 나올 경우,

##### 1-1. Clib 설치
> sudo apt install rpm

#### 2. 설치 확인
example) 
> vi hello.c

'#include <stdio.h>

int main()

{

    printf("hello world!!");

    return 0;

}'

> gcc -v -o filename filename.c
>./hello

실행 시, hello world!!가 나오면 설치 완료

