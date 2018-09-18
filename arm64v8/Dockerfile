FROM arm64v8/ubuntu:16.04

ENV CAFFE_ROOT=/opt/caffe
WORKDIR $CAFFE_ROOT
ARG CLONE_TAG=master

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential\
    git\
	cmake\
    ca-certificates openssl \
    libboost-all-dev\
    libprotobuf-dev\
    libleveldb-dev\
    libsnappy-dev\
    libopencv-dev\
    libhdf5-serial-dev\
    protobuf-compiler\
    libatlas-base-dev\
    libgflags-dev\
    libgoogle-glog-dev\
    liblmdb-dev&&\
    rm -rf /var/lib/apt/lists/* &&\
    git clone https://github.com/BVLC/caffe.git . &&\
    cp Makefile.config.example Makefile.config && \
    mkdir build && cd build && \
    cmake -DCPU_ONLY=ON -DBUILD_python=OFF -DBUILD_docs=OFF .. && \
    make all -j"$(nproc)" &&\
    make install