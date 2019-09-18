FROM ubuntu:xenial

ARG CMAKE_V_MAJOR="3"
ARG CMAKE_V_MINOR="13"
ARG CMAKE_V_PATCH="5"
ARG CMAKE_VERSION=${CMAKE_V_MAJOR}.${CMAKE_V_MINOR}.${CMAKE_V_PATCH}
ARG CLANG_VERSION="8.0.1"

RUN apt-get update \
 && apt-get install -y \
    build-essential \
    wget \
    xz-utils \
 && apt-get clean \
# CMake
 && wget https://cmake.org/files/v${CMAKE_V_MAJOR}.${CMAKE_V_MINOR}/cmake-${CMAKE_VERSION}-Linux-x86_64.sh \
 && sh cmake-${CMAKE_VERSION}-Linux-x86_64.sh --skip-license \
 && rm cmake-${CMAKE_VERSION}-Linux-x86_64.sh \
# Clang
 && mkdir -p /tmp/clang \
 && cd /tmp/clang \
 && wget http://releases.llvm.org/${CLANG_VERSION}/clang+llvm-${CLANG_VERSION}-x86_64-linux-gnu-ubuntu-16.04.tar.xz \
 && tar xvf clang+llvm-${CLANG_VERSION}-x86_64-linux-gnu-ubuntu-16.04.tar.xz \
 && cp -R clang+llvm-${CLANG_VERSION}-x86_64-linux-gnu-ubuntu-16.04/* /usr \
 && cd /usr/bin \
 && ln -s clang-6.0 clang++-6.0 \
 && update-alternatives --install /usr/bin/clang   clang   /usr/bin/clang-6.0 999 \
 && update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-6.0 999 \
 && update-alternatives --install /usr/bin/cc  cc  /usr/bin/clang-6.0 999 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-6.0 999 \
 && rm -r /tmp/clang
