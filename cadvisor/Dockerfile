#
# Dockerfile for cadvisor
#

FROM alpine:edge
MAINTAINER kev <noreply@easypi.pro>

ENV CADVISOR_VERSION 0.23.4

RUN set -xe \
    # To insatll packages in alphine box
    && apk add --no-cache ca-certificates openssl device-mapper zfs \
    # To retrive the content of the web server
    && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-2.23-r3.apk \
    && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.23-r3/glibc-bin-2.23-r3.apk \
    # install below apk
    && apk add --allow-untrusted glibc-2.23-r3.apk glibc-bin-2.23-r3.apk \
    # remove files with .apk
    && rm -f *.apk

RUN set -xe \
    && wget https://github.com/google/cadvisor/releases/download/v${CADVISOR_VERSION}/cadvisor -O /usr/bin/cadvisor \
    && chmod +x /usr/bin/cadvisor

EXPOSE 8080

ENTRYPOINT ["cadvisor", "-logtostderr"]
