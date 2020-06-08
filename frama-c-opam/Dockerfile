FROM ocaml/opam2:4.12

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "08-06-2020"
LABEL author "Florian Stosse"
LABEL description "Opam2 v4.12 image, with Frama-C Calcium (20.0)"
LABEL license "MIT license"

RUN \
  opam update && \
  sudo apt-get update && \
  opam depext frama-c && \
  opam install frama-c