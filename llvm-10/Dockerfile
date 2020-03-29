FROM ubuntu:19.10

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "29-03-2020"
LABEL author "Florian Stosse"
LABEL description "LLVM 10.0.0, using Ubuntu 19.10 base image"
LABEL license "MIT license"

RUN \
  apt update && \
  # Needed to import the LLVM repo key and handle the HTTPS cert
  apt install gnupg2 ca-certificates -y

ADD https://apt.llvm.org/llvm-snapshot.gpg.key /tmp
ADD llvm.list /etc/apt/sources.list.d

RUN \
  apt-key add /tmp/llvm-snapshot.gpg.key && \
  apt update && \
  apt install clang-10 lldb-10 lld-10 -y && \
  # Try to regain some space in the final image, and clean temporary files
  apt-get clean && \
  rm -rf /tmp/* && rm -rf /var/lib/apt/lists/*

# Start from a Bash prompt
CMD [ "/bin/bash" ]