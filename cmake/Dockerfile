# Source: https://hub.docker.com/_/gcc/
FROM gcc:11.1.0

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "07-05-2021"
LABEL author "Florian Stosse"
LABEL description "CMake 3.20.2 using GCC 11.1 base image"
LABEL license "MIT license"

# Cf. https://github.com/Kitware/CMake/releases
ARG CMAKE_VERSION=3.20.2

RUN wget --no-check-certificate https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-linux-x86_64.sh \
  -q -O /tmp/cmake-install.sh && \
  chmod u+x /tmp/cmake-install.sh && \
  mkdir /usr/bin/cmake && \
  /tmp/cmake-install.sh --skip-license --prefix=/usr/bin/cmake && \
  rm /tmp/cmake-install.sh

ENV PATH="/usr/bin/cmake/bin:${PATH}"