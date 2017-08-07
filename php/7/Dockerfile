FROM daocloud.io/php:7-apache

RUN echo 'hello' \
	&& apt-get update \
	&& apt-get install openssl  libssl-dev \
	&& pecl install mongodb \
	&& echo "extension=mongodb.so" >> /usr/local/etc/php/php.ini


# docker build -t jfphp7 .
# docker run -d -p 8085:80 -v /Users/jafar/phproot:/var/www/html --name php71 jfphp7