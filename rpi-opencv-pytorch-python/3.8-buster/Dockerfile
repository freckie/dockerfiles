# OpenCV 4 for Python3 on Raspberry Pi

# Reference 
# https://gist.github.com/akaanirban/621e63237e63bb169126b537d7a1d979

FROM freckie/rpi-opencv-python:3.8-buster

LABEL maintainer="freckie@frec.kr"

RUN apt install -y libopenblas-dev libblas-dev m4 cmake cython python3-yaml libatlas-base-dev
RUN pip3 install pyyaml

RUN export USE_CUDA=0 && \
    export USE_MKLDNN=0 && \
    export USE_NNPACK=0 && \
    export USE_QNNPACK=0 && \
    export USE_NUMPY=1 && \
    export USE_DISTRIBUTED=0 && \
    export NO_CUDA=1 && \
    export NO_DISTRIBUTED=1 && \
    export NO_MKLDNN=1 && \
    export NO_NNPACK=1 && \
    export NO_QNNPACK=1 && \
    export ONNX_ML=1

WORKDIR /root
RUN git clone --recursive https://github.com/pytorch/pytorch && \
    cd pytorch

WORKDIR /root/pytorch
RUN python3 setup.py build && \
    python3 setup.py install

RUN pip3 install torchvision==0.7.0

WORKDIR /root
