# FROM daocloud.io/php:7-apache
FROM daocloud.io/php:5.6-apache

RUN echo 'hello' \
    && echo "Asia/Shanghai" > /etc/timezone \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	# && apt-get update \
	# && apt-get install -y openssl  libssl-dev \
	# && pecl install mongodb \
	# && echo "extension=mongodb.so" >> /usr/local/etc/php/php.ini


# docker build -t jfphp56 .
# docker run -d -p 8086:80 -v /Users/jafar/phproot:/var/www/html --name php56 jfphp56
# docker run -d -p 8086:80 -v F:/jafar/workspace/php:/var/www/html --name php56 jfphp56