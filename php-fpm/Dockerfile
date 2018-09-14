FROM php:7.2-fpm
RUN docker-php-ext-install mysqli pdo pdo_mysql bcmath
RUN apt-get update && apt-get install -y libmemcached-dev zlib1g-dev \
    && pecl install memcached-3.0.2 \
    && docker-php-ext-enable memcached
