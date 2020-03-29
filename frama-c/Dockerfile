FROM ubuntu:19.10 as builder

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "18-03-2020"
LABEL author "Florian Stosse"
LABEL description "Ubuntu 19.10 image, with Frama-C Calcium (20.0)"
LABEL license "MIT license"

RUN sed -i 's/# deb-src/deb-src/g' /etc/apt/sources.list
RUN apt update
RUN apt-get build-dep frama-c -y
RUN apt install wget libyojson-ocaml-dev libwhy3-ocaml-dev -y

WORKDIR /tmp
RUN wget https://frama-c.com/download/frama-c-20.0-Calcium.tar.gz
RUN tar -xf frama-c-20.0-Calcium.tar.gz

WORKDIR /tmp/frama-c-20.0-Calcium
RUN CFLAGS="-static" LDFLAGS="-static" ./configure --disable-gui
RUN make

FROM ubuntu:19.10
COPY --from=builder /tmp/frama-c-20.0-Calcium/ /tmp/frama-c-20.0-Calcium/
WORKDIR /tmp/frama-c-20.0-Calcium/

RUN \
    apt update && \
    apt install ocaml-findlib make libocamlgraph-ocaml-dev libzarith-ocaml libyojson-ocaml libwhy3-ocaml-dev -y && \
    make install && \
    rm -rf /tmp/frama-c-20.0-Calcium/ && \
    apt-get clean