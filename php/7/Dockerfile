FROM registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1

RUN echo "hello 1.1" \
	&& cd /var/lib \
	&& php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
	&& php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
	&& php composer-setup.php \
	&& php -r "unlink('composer-setup.php');" \
	&& ln -s /var/lib/composer.phar /usr/bin/composer \
	&& composer --version

# cd php/7
# docker build -t jfphp7 .
# docker run -d -p 8085:80 -v /Users/jafar/phproot:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1
# docker run -d -p 8085:80 -v /storage/www/php:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1
# docker run -d -p 8085:80 -v F:/jafar/workspace/php:/var/www/html --name php71 registry.cn-hangzhou.aliyuncs.com/open/jfphp7:1.1