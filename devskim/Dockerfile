FROM ubuntu:19.10

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "16-04-2020"
LABEL author "Florian Stosse"
LABEL description "DevSkim tool v0.4.119 using Ubuntu 19.10 base image"
LABEL license "MIT license"

COPY DevSkim_Linux /usr/devskim/

RUN \
    apt update && \
    apt install libicu63 -y && \
    ln -s /usr/devskim/devskim /bin/devskim