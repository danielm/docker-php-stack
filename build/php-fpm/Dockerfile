FROM php:7.4-fpm-alpine

COPY ./php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

RUN apk --update --no-cache add bash git libxml2-dev oniguruma-dev icu-dev

RUN docker-php-ext-install opcache
RUN docker-php-ext-install intl
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install sysvsem
RUN docker-php-ext-install ctype
RUN docker-php-ext-install iconv
RUN docker-php-ext-install json
RUN docker-php-ext-install session
RUN docker-php-ext-install simplexml
RUN docker-php-ext-install tokenizer
RUN docker-php-ext-install mbstring

COPY --from=composer /usr/bin/composer /usr/bin/composer
COPY --from=symfonycorp/cli symfony /usr/bin/symfony

RUN mkdir /.symfony && chown 1000:1000 /.symfony

WORKDIR /var/www

# TODO: Here we could add run some extra comands like running db migrations (?)
CMD composer install ;  php-fpm 

EXPOSE 9000

