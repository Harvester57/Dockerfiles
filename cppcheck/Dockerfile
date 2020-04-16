FROM alpine:3.11 AS builder

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "16-04-2020"
LABEL author "Florian Stosse"
LABEL description "CppCheck v1.90, built using latest Alpine image"
LABEL license "MIT license"

RUN \
	apk add --no-cache -t .required_apks git make g++ pcre-dev && \
	mkdir -p /usr/src /src

WORKDIR /usr/src

RUN	git clone https://github.com/danmar/cppcheck.git

WORKDIR /usr/src/cppcheck

RUN	\
	git checkout 1.90 && \
	make install FILESDIR=/cfg HAVE_RULES=yes CXXFLAGS="-O2 -DNDEBUG --static" -j `getconf _NPROCESSORS_ONLN` && \
	strip /usr/bin/cppcheck

FROM alpine:3.11.5

COPY --from=builder /usr/bin/cppcheck /usr/bin/cppcheck
