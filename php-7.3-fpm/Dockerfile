#Make some argrument first
ARG VERSION=7.3

#Get PHP image
FROM php:${VERSION}-fpm

#Compile some PHP Module
RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd \
	&& docker-php-ext-install -j$(nproc) gd

RUN apt-get update && apt-get install -y \
        libmcrypt-dev \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt

RUN docker-php-ext-configure mysqli \
    && docker-php-ext-install -j$(nproc) mysqli

RUN apt-get update && apt-get install -y \
        libxml2-dev \
    && docker-php-ext-configure xmlrpc \
    && docker-php-ext-install -j$(nproc) xmlrpc

RUN apt-get update && apt-get install -y \
        libzip-dev \
    && docker-php-ext-configure zip \
    && docker-php-ext-install -j$(nproc) zip

RUN docker-php-ext-configure opcache \
    && docker-php-ext-install -j$(nproc) opcache

RUN apt-get autoremove -y