# FROM registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.0

# RUN echo 'この世の全ての不利益は当人の能力不足!' \
# 	&& pwd \
# 	&& php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
# 	&& php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
# 	&& php composer-setup.php \
# 	&& php -r "unlink('composer-setup.php');" \
# 	&& ls -lah \
# 	&& apt-get update \
# 	&& apt-get install -y git \
# 	&& git --version \
# 	&& mv /var/www/html/composer.phar /var/lib/composer.phar \
# 	&& ln -s /var/lib/composer.phar /usr/bin/composer \
# 	&& composer --version \
# 	&& composer config -g repo.packagist composer https://packagist.phpcomposer.com

# cd php/7
# docker build -t jfphp7 .
# docker run -d -p 8085:80 -v /Users/jafar/phproot:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1
# docker run -d -p 8085:80 -v /storage/www/php:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1
# docker run -d -p 8085:80 -v F:/jafar/workspace/php:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1

# この世の全ての不利益は当人の能力不足

FROM registry.cn-hangzhou.aliyuncs.com/open/alpine

MAINTAINER jafar.tang<461415520@qq.com>

ENV TIMEZONE Asia/Shanghai
ENV PHP_MEMORY_LIMIT 512M
ENV MAX_UPLOAD 50M
ENV PHP_MAX_FILE_UPLOAD 200
ENV PHP_MAX_POST 100M
ENV PHP_REDIS=3.1.4

#基础依赖
RUN apk add php7 \
    php7-common php7-intl php7-gd php7-mcrypt php7-openssl \
    php7-gmp php7-json php7-dom php7-pdo php7-zip \
    php7-zlib php7-mysqli php7-bcmath php7-pdo_mysql php7-pgsql \
    php7-pdo_pgsql php7-gettext php7-xmlreader php7-xmlrpc \
    php7-bz2 php7-iconv php7-curl php7-ctype php7-fpm \
    php7-mbstring php7-session php7-phar curl curl-dev postgresql-dev \
    ## 如果使用swoole  需要取消下行注释
   # hiredis-dev libmcrypt-dev gmp-dev icu-dev linux-headers musl --virtual .phpize-deps $PHPIZE_DEPS \
    tzdata && \
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/local/bin/composer && \
    composer self-update && \
    sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php7/php-fpm.conf && \
    sed -i -e "s/listen\s*=\s*127.0.0.1:9000/listen = 9000/g" /etc/php7/php-fpm.d/www.conf && \
    sed -i "s|;date.timezone =.*|date.timezone = ${TIMEZONE}|" /etc/php7/php.ini && \
    sed -i "s|memory_limit =.*|memory_limit = ${PHP_MEMORY_LIMIT}|" /etc/php7/php.ini && \
    sed -i "s|upload_max_filesize =.*|upload_max_filesize = ${MAX_UPLOAD}|" /etc/php7/php.ini && \
    sed -i "s|max_file_uploads =.*|max_file_uploads = ${PHP_MAX_FILE_UPLOAD}|" /etc/php7/php.ini && \
    sed -i "s|post_max_size =.*|max_file_uploads = ${PHP_MAX_POST}|" /etc/php7/php.ini && \
    sed -i "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/" /etc/php7/php.ini && \
    sed -i "s/;extension=php_pgsql.so/extension=php_pgsql.so/" /etc/php7/php.ini && \
    sed -i "s/;extension=php_pdo_pgsql.so/extension=php_pdo_pgsql.so/" /etc/php7/php.ini && \
    mkdir -p /usr/src/php/ext/redis && \
    curl -L https://github.com/phpredis/phpredis/archive/$PHP_REDIS.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 && \
    echo 'redis' >> /usr/src/php-available-exts && \
    docker-php-ext-install redis pgsql pdo pdo_mysql pdo_pgsql && \
      rm -rf /var/cache/apk/*

WORKDIR /www

EXPOSE 9000

CMD [ "php-fpm" ]

# RUN echo 'hello world' \
# 	&& apk add php7 \
# 	&& apk add php7-mysqli php7-pdo_mysql php7-mbstring php7-json php7-zlib php7-gd php7-intl php7-session \
# 	&& php -v