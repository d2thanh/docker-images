#Make some argrument first
ARG VERSION=7.4

#Get PHP image
FROM php:${VERSION}-fpm-alpine

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions gd mcrypt mysqli xmlrpc zip opcache memcache