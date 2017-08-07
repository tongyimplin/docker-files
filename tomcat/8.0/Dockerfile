FROM tomcat:8.0

MAINTAINER jafar.tang

# this could be run multi times
#RUN echo 'helloworld'

# the logined user who start the system
USER root

# the ports which will exposed to external
EXPOSE 8080 8958 8000

# add local file to image
#ADD ./ /app
#ADD ./java.security /etc/java-8-openjdk/security/

# mount point volumn
#VOLUMN

# work dir
#WORKDIR /var/

# ENV

# this is only run one times
RUN pwd \
    && echo "Asia/Shanghai" > /etc/timezone \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && sed "s/securerandom.source=file:\/dev\/random/securerandom.source=file:\/dev\/urandom/g" /etc/java-8-openjdk/security/java.security


# everything is ready to build