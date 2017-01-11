FROM php:7.1-fpm

RUN apt-get clean -y
# Install the PHP extensions we need
RUN apt-get update && \
apt-get install -y --no-install-recommends \
    curl \
    mysql-client \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libicu-dev \
    libssl-dev \
    libmcrypt-dev && \
    docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr && \
    docker-php-ext-install gd pdo_mysql mysqli opcache intl bcmath zip && \
    docker-php-ext-enable bcmath zip pdo_mysql
RUN pecl install redis -y
RUN docker-php-ext-enable redis
##install composer
# Setup the Composer installer
RUN php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php \
		&& php composer-setup.php \
		&& php -r "unlink('composer-setup.php');" \
		&& mv composer.phar /usr/local/bin/composer
#drush command
ADD extra/drush /usr/sbin/drush

VOLUME /app/web
WORKDIR /app/web
