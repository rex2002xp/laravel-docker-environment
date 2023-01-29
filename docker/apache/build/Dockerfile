FROM php:8-apache-bullseye

WORKDIR /var/www/html

RUN apt-get update && apt-get upgrade -y && apt-get install -y curl \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && curl -sL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install nodejs

RUN a2enmod rewrite

RUN service apache2 restart

