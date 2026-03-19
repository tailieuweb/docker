FROM php:8.3.21-apache

ENV COMPOSER_VERSION=2.8.9
ENV TZ Asia/Tokyo
ENV APACHE_DOCUMENT_ROOT /var/www/html

RUN apt-get update \
    && apt-get install -y \
        curl \
        zip \
        unzip \
        git \
        supervisor \
        libpng-dev \
        libzip-dev \
        libicu-dev \
        libxml2-dev \
        libonig-dev \
        tzdata \
    && docker-php-ext-install \
        mysqli \
        pdo_mysql \
        intl \
        xml \
        gd \
        zip \
        opcache \
        bcmath \
        sockets

# Xdebug (optional)
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Apache config
RUN a2enmod rewrite

# Set document root (Moodle KHÔNG dùng /public)
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- \
    --install-dir=/usr/local/bin \
    --filename=composer \
    --version=$COMPOSER_VERSION

# User
RUN useradd -ms /bin/bash -u 1000 app