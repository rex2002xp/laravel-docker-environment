FROM php:8.2.1-fpm-alpine3.17

RUN apk add --update linux-headers && \
    apk add --no-cache $PHPIZE_DEPS && \
    pecl install xdebug && \
    docker-php-ext-enable xdebug

RUN docker-php-ext-install pdo pdo_mysql
