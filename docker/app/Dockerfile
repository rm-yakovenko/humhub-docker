FROM php:7-fpm

RUN apt-get -y -qq update
RUN apt-get -y -qq install  autoconf g++ make openssl libssl-dev libcurl4-openssl-dev libpng-dev libicu-dev git libldb-dev libldap2-dev libxml2-dev libjpeg-dev libfreetype6-dev
RUN ln -s /usr/lib/x86_64-linux-gnu/libldap.so /usr/lib/libldap.so
RUN docker-php-ext-install -j4 gd curl iconv json intl opcache xml phar zip ldap pdo_mysql exif

RUN rm -rf /var/cache/apt/* && rm -rf /tmp/*

ADD app.ini /usr/local/etc/php/conf.d
ADD xdebug.ini /usr/local/etc/php/conf.d
ADD www.conf /usr/local/etc/php-fpm.d

RUN curl -Lo /usr/local/bin/composer https://getcomposer.org/composer.phar
RUN chmod +x /usr/local/bin/composer

RUN composer global require "fxp/composer-asset-plugin:^1.2.0"

RUN useradd app

CMD ["php-fpm", "-F"]

EXPOSE 9000