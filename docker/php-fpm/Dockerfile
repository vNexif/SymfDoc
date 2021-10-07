ARG VERSION
#Dev section
FROM php:${VERSION}-fpm-alpine AS dev

RUN apk update && \
    apk add --no-cache --virtual dev-deps git autoconf gcc g++ make && \
    apk add --no-cache zlib-dev libzip-dev 
    
RUN apk --no-cache add nodejs yarn --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community

RUN pecl install xdebug && \
    docker-php-ext-enable xdebug && \
    docker-php-ext-install pdo_mysql zip

COPY ./docker/php-fpm/default.ini /usr/local/etc/php/conf.d/default.ini


ENV APP_ENV=dev
WORKDIR /app

RUN wget https://getcomposer.org/installer && \
    php installer --install-dir=/usr/local/bin/ --filename=composer && \
    rm installer

#Test section
FROM dev AS test

WORKDIR /app

COPY . .

RUN composer self-update --1

RUN chown -R www-data:www-data .

#Prod section
FROM test as prod

ENV APP_ENV=prod
WORKDIR /app

RUN composer install --no-dev --no-interaction --optimize-autoloader --ignore-platform-reqs

RUN rm /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# Cleanup
RUN apk del dev-deps && \
    rm /usr/local/bin/composer