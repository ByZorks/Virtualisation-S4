FROM wordpress:6.3-php8.1-apache

# Installation des extensions PHP nécessaires
RUN apt-get update && apt-get install -y \
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
RUN curl -O https://raw.githubusercontent.com/wp-cli/wp-cli/master/installer.php \
    && php installer.php --install-dir=/usr/local/bin --filename=wp \
    && chmod +x /usr/local/bin/wp