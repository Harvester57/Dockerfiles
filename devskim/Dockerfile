FROM ubuntu:18.04

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate '03-03-2020'
LABEL author "Florian Stosse"
LABEL vendor "Safran Data Systems"
LABEL description "DevSkim tool using Ubuntu 18.04 base image"
LABEL license "MIT license"

COPY DevSkim_Linux /usr/devskim/

RUN apt update && apt install libicu60 -y && ln -s /usr/devskim/devskim /bin/devskim