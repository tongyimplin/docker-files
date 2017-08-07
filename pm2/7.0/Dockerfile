FROM keymetrics/pm2-docker-alpine:7

MAINTAINER jafar.tang<461415520@qq.com>

# this could be run multi times
#RUN echo 'helloworld'

# the logined user who start the system
USER root

# the ports which will exposed to external
#EXPOSE

RUN pwd \
    && npm -v \
    && node -v \
    && echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.4/main" > /etc/apk/repositories \
    && apk update && apk add curl bash tree tzdata \
    && cp -r -f /usr/share/zoneinfo/Hongkong /etc/localtime \
    && echo -ne "Alpine Linux 3.4 image. (`uname -rsv`)\n" >> /root/.built