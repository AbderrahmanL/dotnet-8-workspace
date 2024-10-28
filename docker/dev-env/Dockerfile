# [Choice] .NET version: 7.0, 6.0, 5.0, 3.1, 6.0-bullseye, 5.0-bullseye, 3.1-bullseye, 6.0-focal, 5.0-focal, 3.1-focal
ARG VARIANT="8.0"
FROM mcr.microsoft.com/vscode/devcontainers/dotnet:${VARIANT}

RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get -qy full-upgrade && \
    apt-get install -qy curl && \
    apt-get -y install --no-install-recommends vim
    
RUN dotnet tool install --global dotnet-ef --version 8.*
ENV PATH $PATH:/root/.dotnet/tools

RUN wget -O dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/853490db-6fd3-4c17-ad8e-9dbb61261252/3d36d7d5b861bbb219aa1a66af6e6fd2/dotnet-sdk-8.0.403-linux-arm64.tar.gz \
&& dotnet_sha512='f42e1ba9a897f91c8d734b09a9bfc82428f0629b7cdd9375262158d9f282797c199558c37ae7f36947e57d8adc61af9490595c4e6bbd05217fd6d05133dded4d' \
&& echo "$dotnet_sha512 dotnet.tar.gz" | sha512sum -c - \
&& mkdir -p /usr/share/dotnet \
&& tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
&& rm dotnet.tar.gz