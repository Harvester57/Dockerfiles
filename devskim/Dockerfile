FROM mcr.microsoft.com/dotnet/core/runtime:3.1-alpine

LABEL maintainer "florian.stosse@safrangroup.com"
LABEL lastupdate "23-11-2020"
LABEL author "Florian Stosse"
LABEL description "DevSkim tool v0.6.1 using .NET Core Runtime Alpine image"
LABEL license "MIT license"

WORKDIR /app
# Cf. https://github.com/microsoft/DevSkim/releases
COPY DevSkim/ .

ENTRYPOINT ["dotnet", "devskim.dll"]