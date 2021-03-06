FROM centos:7
MAINTAINER Asher Dawes asher.dawes@gmail.com

RUN yum update -y && \
    yum install -y \
    autoconf \
    libtool \
    unzip \
    epel-release \
    git \
    python \
    python34-devel \
    make \
    wget \
    curl-devel \
    libcurl-devel \
    automake \
    gcc \
    gcc-c++ \
    patch \
    which \
    glibc-static \
    libstdc++-static \
    centos-release-scl-rh && \
    yum install -y devtoolset-7 \
    devtoolset-7-binutils-devel \
    lbzip2 && \
    cd /home && \
    wget https://download.oracle.com/berkeley-db/db-6.2.32.tar.gz && \
    tar -xf db-6.2.32.tar.gz &&      \
    cd db-6.2.32/build_unix  &&      \
    ../dist/configure --prefix=/usr  \
                --enable-compat185   \
                --enable-dbm         \
                --disable-static     \
                --enable-cxx &&      \
    make && \
    make docdir=/usr/share/doc/db-6.2.32 install && \
    chown -v -R root:root            \
      /usr/bin/db_*                  \
      /usr/include/db{,_185,_cxx}.h  \
      /usr/lib/libdb*.{so,la}        \
      /usr/share/doc/db-6.2.32    && \ 
    cd ../.. && \
    wget https://www.zlib.net/zlib-1.2.11.tar.gz && \
    tar -xf zlib-1.2.11.tar.gz && \
    cd zlib-1.2.11 && \
    export CFLAGS=-fPIC && \
    ./configure --prefix=/usr --shared --libdir=/lib --static && \
    make test && \
    make install && \
    cd .. && \
    rm -Rf zlib-1.2.11 && \
    wget http://curl.haxx.se/download/curl-7.64.0.tar.gz && \
    tar xf curl-7.64.0.tar.gz && \
    cd curl-7.64.0 && \
    ./configure --disable-shared --enable-static --prefix=/tmp/curl --disable-ldap --disable-sspi --without-librtmp --disable-ftp --disable-file --disable-dict --disable-telnet --disable-tftp --disable-rtsp --disable-pop3 --disable-imap --disable-smtp --disable-gopher --disable-smb --without-libidn && \
    make && \
    make install && \
    cd .. && \
    rm -Rf curl-7.64.0 && \
    update-alternatives --install /usr/bin/gcc-7.3 gcc-7.3 /opt/rh/devtoolset-7/root/usr/bin/gcc 10 && \
    update-alternatives --install /usr/bin/g++-7.3 g++-7.3 /opt/rh/devtoolset-7/root/usr/bin/g++ 10 && \
    scl enable devtoolset-7 sh && \
    source /opt/rh/devtoolset-7/enable

ENV CC=/opt/rh/devtoolset-7/root/usr/bin/gcc \
    CXX=/opt/rh/devtoolset-7/root/usr/bin/g++

VOLUME /home
WORKDIR /home

