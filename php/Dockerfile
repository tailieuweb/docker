FROM php:8.3.21-apache

ENV COMPOSER_VERSION=2.8.9
ENV TZ Asia/Tokyo
ENV APACHE_DOCUMENT_ROOT /var/www/html/public

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
        libcurl4-openssl-dev \
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
        sockets \
        mbstring \
        exif \
        pcntl \
        soap \
    && docker-php-ext-enable opcache

RUN echo "zend.exception_ignore_args = On" >> /usr/local/etc/php/php.ini
RUN echo "display_errors = Off" >> /usr/local/etc/php/php.ini \
    && echo "log_errors = On" >> /usr/local/etc/php/php.ini \
    && echo "memory_limit = 512M" >> /usr/local/etc/php/php.ini \
    && echo "max_execution_time = 300" >> /usr/local/etc/php/php.ini

RUN echo "max_input_vars = 5000" >> /usr/local/etc/php/php.ini

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