FROM debian:buster

LABEL maintainer="helto4real <helto4real@joysoftware.xyz>"

WORKDIR /opt/vlang

ENV VVV  /opt/vlang
ENV PATH /opt/vlang:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

RUN mkdir -p /opt/vlang && ln -s /opt/vlang/v /usr/bin/v

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends gcc clang  libssl-dev libsqlite3-dev make git valgrind nodejs npm libx11-dev libglfw3-dev libfreetype6-dev openssh-client && \
    apt-get clean && rm -rf /var/cache/apt/archives/* && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/vlang/v /opt/vlang && make && v -version

RUN mkdir /home/projects
WORKDIR /home/projects

ENTRYPOINT ["/bin/bash"]