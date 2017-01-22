FROM zterry95/docker-php7:5-base
RUN pecl install memcached 
RUN docker-php-ext-enable memcached

RUN pecl install redis
RUN docker-php-ext-enable redis

RUN pecl install xhprof-beta
RUN docker-php-ext-enable xhprof 


VOLUME /app/web
WORKDIR /app/web
