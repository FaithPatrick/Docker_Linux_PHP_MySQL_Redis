######
# See: https://hub.docker.com/_/php/
######

FROM php:7.1.11-fpm
#RUN usermod -u 1000 www-data
MAINTAINER Patrick95 <patrick95@foxmail.com>

######
# You can install php extensions using docker-php-ext-install
######

ADD ./sources.list /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt mysqli pdo_mysql\
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && pecl install redis-3.1.0 \
    && docker-php-ext-enable redis