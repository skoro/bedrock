FROM php:8.0-fpm

# Install development dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip libzip-dev \
        libpng-dev libjpeg62-turbo-dev libfreetype6-dev libwebp-dev \
        libicu-dev libmagickwand-dev

# Clear package cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# PHP extensions
RUN pecl install xdebug && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd --with-jpeg --with-webp --with-freetype \
    && docker-php-ext-install -j$(nproc) opcache pdo_mysql mysqli bcmath zip gd exif intl sockets \
    && pecl install imagick && docker-php-ext-enable imagick \
    && pecl install apcu && docker-php-ext-enable apcu

RUN rm -rf /tmp/*

# Get the latest composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# COPY php-app.ini /usr/local/etc/php/conf.d/

WORKDIR /var/www

EXPOSE 9000
