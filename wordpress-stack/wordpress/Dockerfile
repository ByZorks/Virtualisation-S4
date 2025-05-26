FROM wordpress:6.3-php8.1-apache

# Installation des extensions PHP nécessaires
RUN apt-get update && apt-get install -y \
    default-mysql-client \
    redis-tools \
    libzip-dev \
    zip \
    unzip \
    && docker-php-ext-install zip

# Installation de l'extension Redis pour PHP
RUN pecl install redis \
    && docker-php-ext-enable redis

# Configuration personnalisée de PHP
COPY php.ini /usr/local/etc/php/conf.d/custom.ini

# Installation de WP-CLI
RUN curl -O https://github.com/wp-cli/wp-cli/releases/download/v2.12.0/wp-cli-2.12.0.phar \
    && chmod +x wp-cli-2.12.0.phar \
    && mv wp-cli-2.12.0.phar /usr/local/bin/wp