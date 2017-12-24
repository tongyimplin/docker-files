FROM alpine:3.6

MAINTAINER jafar.tang <461415520@qq.com>

# ADD source dest

# RUN apk update \

RUN apk update && apk add curl bash tree tzdata vim \
    && cp -r -f /usr/share/zoneinfo/Hongkong /etc/localtime \
    && echo -ne "Alpine Linux 3.4 image. (`uname -rsv`)\n" >> /root/.built