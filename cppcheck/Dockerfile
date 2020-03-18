FROM alpine:latest

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate '18-03-2020'
LABEL author "Florian Stosse"
LABEL vendor "Safran Data Systems"
LABEL description "CppCheck tool, built using latest Alpine image"
LABEL license "MIT license"

RUN \
	apk add --no-cache -t .required_apks git make g++ pcre-dev && \
	mkdir -p /usr/src /src && cd /usr/src && \
	git clone https://github.com/danmar/cppcheck.git && \
	cd cppcheck && \
	make install FILESDIR=/cfg HAVE_RULES=yes CXXFLAGS="-O2 -DNDEBUG --static" -j `getconf _NPROCESSORS_ONLN` && \
	strip /usr/bin/cppcheck && \
	apk del .required_apks && \
	rm -rf /usr/src
