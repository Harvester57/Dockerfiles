FROM alpine:3.12 AS builder

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "16-06-2020"
LABEL author "Florian Stosse"
LABEL description "CppCheck v2.1, built using latest Alpine image"
LABEL license "MIT license"

RUN \
  apk add --no-cache -t .required_apks git make g++ pcre-dev && \
  mkdir -p /usr/src /src

WORKDIR /usr/src

# Cf. https://github.com/danmar/cppcheck/releases
RUN	git clone --branch 2.1 https://github.com/danmar/cppcheck.git --depth 1

WORKDIR /usr/src/cppcheck

RUN	\
  make install FILESDIR=/cfg HAVE_RULES=yes CXXFLAGS="-O3 -DNDEBUG --static" -j2 && \
  strip /usr/bin/cppcheck

FROM alpine:3.12

COPY --from=builder /usr/bin/cppcheck /usr/bin/cppcheck
ENTRYPOINT ["cppcheck"]