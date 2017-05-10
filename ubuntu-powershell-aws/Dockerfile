FROM ubuntu:latest

ENV POWERSHELL_DOWNLOAD_URL=https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-beta.1/powershell_6.0.0-beta.1-1ubuntu1.16.04.1_amd64.deb

RUN apt-get update \
&& apt-get install -y --no-install-recommends \
libc6 \
libcurl3 \
ca-certificates \
libgcc1 \
libicu55 \
libssl1.0.0 \
libstdc++6 \
libtinfo5 \
libunwind8 \
libuuid1 \
zlib1g \
curl \
git \
&& rm -rf /var/lib/apt/lists/*

RUN curl -L $POWERSHELL_DOWNLOAD_URL --output powershell_linux.deb
RUN dpkg -i powershell_linux.deb
RUN rm powershell_linux.deb

RUN powershell -command "Install-Module -Name AwsPowerShell.NetCore -Force -Verbose"

ENTRYPOINT [ "powershell" ]