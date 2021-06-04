FROM arm64v8/ubuntu:16.04
LABEL maintainer "Takuya Takeuchi <takuya.takeuchi.dev@gmail.com>"

# install package to build
RUN apt-get update && apt-get install -y \
    build-essential \
    libx11-dev \
    libgtk2.0-dev \
    pkg-config \
    cmake

# set compiler
ENV CMAKE_C_COMPILER=/usr/bin/gcc
ENV CMAKE_CXX_COMPILER=/usr/bin/g++

# Install powershell (needs 7.1 for arm)
# Deps: https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7.1#binary-archives
RUN apt-get install -y \
    libc6 libgcc1 libgssapi-krb5-2 liblttng-ust0 libstdc++6 \
    libcurl3 libunwind8 libuuid1 zlib1g libssl1.0.0 libicu55 \
    wget && \
    wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.3/powershell-7.1.3-linux-arm64.tar.gz
RUN mkdir /usr/share/powershell && \
    tar xvf powershell-7.1.3-linux-arm64.tar.gz -C /usr/share/powershell && \
    ln -s /usr/share/powershell/pwsh /usr/bin/pwsh && \
    rm powershell-7.1.3-linux-arm64.tar.gz