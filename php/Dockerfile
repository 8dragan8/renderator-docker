FROM php:7.4-fpm-alpine

# Application environment variable
ARG APP_ENV
# Install Additional dependencies
RUN apk update && apk add --no-cache $PHPIZE_DEPS \
   make nasm autoconf automake libtool dpkg pkgconfig libpng libpng-dev g++ \
   build-base shadow nano curl gcc git bash zip libzip-dev
# php7 \
# php7-fpm \
# php7-common \
# php7-pdo \
# php7-pdo_mysql \
# php7-mysqli \
# php7-mcrypt \
# php7-mbstring \
# php7-xml \
# php7-openssl \
# php7-json \
# php7-phar \
# php7-zip \
# php7-gd \
# php7-dom \
# php7-session \
# php7-zlib
# RUN docker-php-ext-configure gd --with-jpeg --with-freetype 
RUN docker-php-ext-install gd 
RUN docker-php-ext-install zip

# Install extensions
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-enable pdo_mysql

# RUN docker-php-ext-install xdebug
# RUN docker-php-ext-enable xdebug

# install xdebug and enable it if the development environment is local
RUN    pecl install xdebug-3.1.5; \
   docker-php-ext-enable xdebug;
# Install PHP Composer
RUN curl -sS https://getcomposer.org/installer | php

RUN mv composer.phar /usr/local/bin/composer
# Remove Cache
RUN rm -rf /var/cache/apk/*
# COPY ./php/php.ini /usr/local/etc/php/

WORKDIR /home/renderator-api-v2

# USER www-data
# RUN composer install
# RUN composer dump-autoload
# RUN php artisan optimize:clear


# RUN chown -R www-data:www-data /home/
EXPOSE 9000

# Run php-fpm
CMD ["php-fpm"]