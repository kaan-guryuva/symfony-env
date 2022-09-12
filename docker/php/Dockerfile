FROM php:8.0-fpm-alpine

RUN apk update \
 && apk add --no-cache $PHPIZE_DEPS \
    bash \
    git \
    zip \
    unzip \
    fish


# PHP extensions
RUN docker-php-ext-install opcache pdo_mysql mysqli
RUN docker-php-ext-enable opcache

# xdebug extensions
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

#NPM
RUN apk add --update nodejs npm

# Composer
WORKDIR /var/www/trive
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN rm -rf /var/cache/apk/*
CMD ["php-fpm", "--nodaemonize"]
