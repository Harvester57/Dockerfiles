FROM ocaml/opam2:4.10

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "29-03-2020"
LABEL author "Florian Stosse"
LABEL description "Opam2 v4.10 image, with Frama-C Calcium (20.0)"
LABEL license "MIT license"

RUN \
  opam update && \
  opam install depext && \
  opam depext frama-c && \
  opam install frama-c.20.0