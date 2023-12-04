# Stage 1: Build stage with PHP and Composer
FROM composer:2 AS composer
WORKDIR /var/www/html
COPY . /var/www/html
RUN composer install --ignore-platform-reqs
RUN composer update

# Stage 2: Final stage with PHP and Apache
FROM php:8.1-apache
WORKDIR /var/www/html
COPY --from=composer /var/www/html /var/www/html

RUN docker-php-ext-install pdo_mysql mysqli
RUN a2enmod rewrite

EXPOSE 8000
