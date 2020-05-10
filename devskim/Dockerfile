FROM ubuntu:20.04

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "10-05-2020"
LABEL author "Florian Stosse"
LABEL description "DevSkim tool v0.4.132 using Ubuntu 19.10 base image"
LABEL license "MIT license"

# Cf. https://github.com/microsoft/DevSkim/releases
COPY DevSkim_Linux /usr/devskim/

RUN \
    apt update && \
    apt install libicu63 -y && \
    ln -s /usr/devskim/devskim /bin/devskim