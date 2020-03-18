FROM mcr.microsoft.com/windows/servercore:ltsc2016 AS builder
SHELL ["cmd", "/S", "/C"]

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate '21-02-2020'
LABEL author "Florian Stosse"
LABEL vendor "Safran Data Systems"
LABEL description "Windows 10 LTSC 2016 image, with Microsoft Build Tools 2017 (v15.0)"
LABEL license "MIT license"

# Set up environment to collect install errors.
ADD https://aka.ms/vscollect.exe C:/TEMP/collect.exe
COPY Install.cmd C:/TEMP

# Download channel for fixed install.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:/TEMP/VisualStudio.chman

ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:/TEMP/vs_buildtools.exe

RUN C:/TEMP/Install.cmd C:/TEMP/vs_buildtools.exe --quiet --wait --norestart --nocache \
--channelUri C:/TEMP/VisualStudio.chman \
--installChannelUri C:/TEMP/VisualStudio.chman \
--add Microsoft.VisualStudio.Workload.VCTools --includeRecommended \
--installPath C:/BuildTools

FROM mcr.microsoft.com/windows/servercore:ltsc2016

COPY --from=builder C:/BuildTools/ C:/BuildTools
COPY ./cp/ C:/cp

# Use developer command prompt and start PowerShell if no other command specified.
ENTRYPOINT C:/BuildTools/Common7/Tools/VsDevCmd.bat &&