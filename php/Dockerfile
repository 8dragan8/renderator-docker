FROM php:7.4-fpm-alpine

# Application environment variable
ARG APP_ENV

# Install Additional dependencies
RUN apk update && apk add --no-cache $PHPIZE_DEPS \
   build-base shadow nano curl gcc git bash \
   php7 \
   php7-fpm \
   php7-common \
   php7-pdo \
   php7-pdo_mysql \
   php7-mysqli \
   php7-mcrypt \
   php7-mbstring \
   php7-xml \
   php7-openssl \
   php7-json \
   php7-phar \
   php7-zip \
   php7-gd \
   php7-dom \
   php7-session \
   php7-zlib

# Install extensions
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-enable pdo_mysql

# install xdebug and enable it if the development environment is local
RUN    pecl install xdebug; \
   docker-php-ext-enable xdebug;
# Install PHP Composer
RUN curl -sS https://getcomposer.org/installer | php

RUN mv composer.phar /usr/local/bin/composer
# Remove Cache
RUN rm -rf /var/cache/apk/*
# COPY ./php/php.ini /usr/local/etc/php/

EXPOSE 9000