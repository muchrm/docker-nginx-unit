FROM debian:jessie
LABEL maintainer="muchrm.me@gmail.com"
RUN apt-get update && apt-get install -y --no-install-recommends\
                gnupg \
                apt-transport-https \
                ca-certificates \
                && rm -rf /var/lib/apt/lists/*

WORKDIR /root

ADD nginx_signing.key .
RUN apt-key add nginx_signing.key

ADD unit.list /etc/apt/sources.list.d
RUN ls /etc/apt/sources.list.d
RUN apt-get update && apt-get install  --no-install-recommends  -y unit && rm -rf /var/lib/apt/lists/*
CMD  ["echo","hello"]