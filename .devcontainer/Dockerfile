# Dockerfile
FROM ubuntu:20.04

RUN apt-get update -y
RUN apt-get install -y software-properties-common lsb-release

# git
RUN apt-get install -y git

# g++
RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN apt-get install -y g++-13
RUN ln -s -f /usr/bin/g++-13 /usr/bin/g++
RUN ln -s -f /usr/bin/gcc-13 /usr/bin/gcc
RUN ln -s -f /usr/bin/gcc-ar-13 /usr/bin/gcc-ar
RUN ln -s -f /usr/bin/gcc-nm-13 /usr/bin/gcc-nm
RUN ln -s -f /usr/bin/gcc-ranlib-13 /usr/bin/gcc-ranlib

# cmake
RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1A127079A92F09ED
RUN apt-add-repository "deb https://apt.kitware.com/ubuntu/ $(lsb_release -cs) main"
RUN apt-get update -y
RUN apt install kitware-archive-keyring
RUN rm /etc/apt/trusted.gpg.d/kitware.gpg
RUN apt-get install -y cmake

RUN apt-get clean all -y && rm -rf /var/lib/apt/lists/*
