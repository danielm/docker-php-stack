FROM php:8.2-fpm-alpine

RUN apk --update --no-cache add git curl bash icu-dev postgresql-dev linux-headers $PHPIZE_DEPS
# libxml2-dev oniguruma-dev

# PHP stuff
RUN docker-php-ext-install intl pdo_pgsql opcache
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
COPY ./conf.d/*.ini /usr/local/etc/php/conf.d/

# Xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

# Composer from official image
COPY --from=composer /usr/bin/composer /usr/local/bin/composer

# Symfony
RUN curl -sS https://get.symfony.com/cli/installer | bash -s -- --install-dir=/usr/local/bin

WORKDIR /var/www

#RUN composer install --no-scripts --no-autoloader

EXPOSE 9000