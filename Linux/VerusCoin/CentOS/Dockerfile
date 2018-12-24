FROM centos:7
MAINTAINER Asher Dawes asher.dawes@gmail.com

RUN yum install -y \
    autoconf \
    libtool \
    unzip \
    git \
    python \
    make \
    wget \
    curl \
    automake \
    gcc \
    gcc-c++ \
    patch \
    glibc-static \
    libstdc++-static && \
    yum install -y centos-release-scl-rh && \
    yum install -y devtoolset-7 && \
    update-alternatives --install /usr/bin/gcc-7.3 gcc-7.3 /opt/rh/devtoolset-7/root/usr/bin/gcc 10 && \
    update-alternatives --install /usr/bin/g++-7.3 g++-7.3 /opt/rh/devtoolset-7/root/usr/bin/g++ 10 && \
    scl enable devtoolset-7 bash
VOLUME /home
WORKDIR /home
