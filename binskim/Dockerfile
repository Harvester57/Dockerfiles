# Source: https://hub.docker.com/_/microsoft-dotnet-core-sdk/
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS builder

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "29-03-2020"
LABEL author "Florian Stosse"
LABEL description "Ubuntu 19.10 image, with BinSkim 1.6.0"
LABEL license "MIT license"

WORKDIR /tmp
RUN git clone --depth 1 https://github.com/microsoft/binskim.git
RUN mkdir /tmp/binary \
    && dotnet publish --configuration Release --framework netcoreapp2.0 --runtime linux-x64 --output /tmp/binary /tmp/binskim/src/BinSkim.Driver/BinSkim.Driver.csproj \
    && chmod +x /tmp/binary/BinSkim

FROM ubuntu:20.04

COPY --from=builder /tmp/binary /usr/share/binskim

RUN ln -s /usr/share/binskim/BinSkim /usr/bin/binskim && \
    apt-get update && \
    apt-get install -y icu-devtools libunwind8 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*