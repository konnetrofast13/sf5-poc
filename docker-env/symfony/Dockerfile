FROM php:7.4-alpine

ARG ONLY_ONE_TIME


# sudo
RUN apk add --no-cache su-exec
RUN set -ex && apk --no-cache add sudo

# install git
RUN apk add --no-cache git

# extensions
RUN apk add icu-dev
RUN docker-php-ext-configure intl && docker-php-ext-install intl
#install composer
# Composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer


COPY php.ini /usr/local/etc/php/


# install symfony
RUN sudo apk add --no-cache bash
RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.alpine.sh' | sudo -E bash
RUN sudo apk add symfony-cli



WORKDIR /var/www/poc

RUN symfony check:requirements


EXPOSE 80

