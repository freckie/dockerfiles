FROM arm32v7/golang:1.15.0-buster

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

RUN go get -u -d gocv.io/x/gocv

RUN apt install -y sudo \
    gcc

RUN cd $GOPATH/src/gocv.io/x/gocv && \
    make install_raspi