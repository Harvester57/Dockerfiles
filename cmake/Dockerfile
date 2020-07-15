FROM gcc:10.1

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "15-07-2020"
LABEL author "Florian Stosse"
LABEL description "CMake 3.17.3 using GCC 10.1 base image"
LABEL license "MIT license"

# Cf. https://github.com/Kitware/CMake/releases
ARG CMAKE_VERSION=3.17.3

RUN \
  wget https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-Linux-x86_64.sh \
  -q -O /tmp/cmake-install.sh && \
  chmod u+x /tmp/cmake-install.sh && \
  mkdir /usr/bin/cmake && \
  /tmp/cmake-install.sh --skip-license --prefix=/usr/bin/cmake && \
  rm /tmp/cmake-install.sh

ENV PATH="/usr/bin/cmake/bin:${PATH}"  