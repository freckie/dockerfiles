# OpenCV 4 for Python3 on Raspberry Pi

# Reference 
# https://www.pyimagesearch.com/2018/09/26/install-opencv-4-on-your-raspberry-pi/

FROM arm32v7/python:3.8-buster

LABEL maintainer="freckie@frec.kr"

RUN apt update -y && apt upgrade -y
RUN apt install -y build-essential \
    cmake \
    pkg-config \
    libjpeg-dev \
    libtiff5-dev \
    libpng-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    libv4l-dev \
    libxvidcore-dev \
    libx264-dev \
    libfontconfig1-dev \
    libcairo2-dev \
    libgdk-pixbuf2.0-dev \
    libpango1.0-dev \
    libgtk2.0-dev \
    libgtk-3-dev \
    libatlas-base-dev \
    gfortran \
    libhdf5-dev \
    libhdf5-serial-dev \
    libhdf5-103 \
    libqtgui4 \
    libqtwebkit4 \
    libqt4-test

WORKDIR /root
RUN wget -O opencv.zip https://github.com/opencv/opencv/archive/4.4.0.zip && \
    wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.4.0.zip

RUN unzip opencv.zip && \
    unzip opencv_contrib.zip && \
    mv opencv-4.4.0 opencv && \
    mv opencv_contrib-4.4.0 opencv_contrib

RUN wget https://bootstrap.pypa.io/get-pip.py && python3 get-pip.py
RUN pip3 install numpy

RUN mkdir /root/opencv/build
WORKDIR /root/opencv/build

RUN cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D OPENCV_ENABLE_NONFREE=ON \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
    -D ENABLE_NEON=ON \
    -D ENABLE_VFPV3=ON \
    -D BUILD_TESTS=OFF \
    -D OPENCV_ENABLE_NONFREE=ON \
    -D INSTALL_PYTHON_EXAMPLES=OFF \
    -D BUILD_EXAMPLES=OFF ..

RUN make -j4 && \
    make install && \
    ldconfig

RUN cd /usr/local/lib/python3.8/site-packages && \
    ln -s /usr/local/python/cv2/python-3.8/cv2.cpython-38m-arm-linux-gnueabihf.so cv2.so
