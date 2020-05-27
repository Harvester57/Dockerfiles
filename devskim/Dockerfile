FROM ubuntu:20.04

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "27-05-2020"
LABEL author "Florian Stosse"
LABEL description "DevSkim tool v0.4.144 using Ubuntu 20.04 base image"
LABEL license "MIT license"

# Cf. https://github.com/microsoft/DevSkim/releases
COPY DevSkim_Linux /usr/devskim/

RUN \
  apt-get update && \
  apt-get install libicu66 -y --no-install-recommends && \
  ln -s /usr/devskim/devskim /bin/devskim && \
  rm -rf /var/lib/apt/lists/*