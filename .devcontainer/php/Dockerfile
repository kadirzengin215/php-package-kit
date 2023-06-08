FROM php:cli

LABEL maintainer="Kadir Zengin"

ARG APP_NAME

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y curl wget git libzip-dev zip unzip

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN groupadd --force -g 1000 $APP_NAME
RUN useradd -ms /bin/bash --no-user-group -g 1000 -u 1337 $APP_NAME

COPY php.ini /usr/local/etc/php/php.ini
COPY conf.d/xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

WORKDIR /usr/src/$APP_NAME
