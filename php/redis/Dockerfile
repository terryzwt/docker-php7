FROM zterry95/docker-php7:7.1-base
RUN pecl install redis -y && docker-php-ext-enable redis

VOLUME /app/web
WORKDIR /app/web
