FROM php:8.1-fpm-alpine

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN mv $PHP_INI_DIR/php.ini-development $PHP_INI_DIR/php.ini

RUN set -ex \
  && apk --no-cache add \
    postgresql-dev

RUN docker-php-ext-install pdo pdo_pgsql

WORKDIR /app/pop-it-mvc

COPY --from=composer/composer:latest-bin /composer /usr/bin/composer

COPY ./pop-it-mvc /app

ENV COMPOSER_ALLOW_SUPERUSER=1

