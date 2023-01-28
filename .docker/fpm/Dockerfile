FROM php:8.2-fpm-alpine

RUN apk --update --no-cache add git curl bash icu-dev postgresql-dev linux-headers $PHPIZE_DEPS
# libxml2-dev oniguruma-dev

# PHP stuff
RUN docker-php-ext-install intl pdo_pgsql opcache
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini
COPY ./php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

# Xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

# Composer from official image
COPY --from=composer /usr/bin/composer /usr/local/bin/composer

# Symfony
RUN curl -sS https://get.symfony.com/cli/installer | bash -s -- --install-dir=/usr/local/bin

#RUN mkdir /.symfony && chown 1000:1000 /.symfony
#RUN echo 'alias sf="php app/console"' >> ~/.bashrc

# RUN ln -s /usr/share/zoneinfo/America/Montevideo /etc/localtime

WORKDIR /var/www

#CMD composer install ;  php-fpm 

EXPOSE 9000