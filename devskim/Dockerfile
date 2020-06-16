FROM mcr.microsoft.com/dotnet/core/runtime:3.1-alpine

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "16-06-2020"
LABEL author "Florian Stosse"
LABEL description "DevSkim tool v0.4.153 using .NET Core Runtime Alpine image"
LABEL license "MIT license"

WORKDIR /app
# Cf. https://github.com/microsoft/DevSkim/releases
COPY DevSkim/ .

ENTRYPOINT ["dotnet", "devskim.dll"]