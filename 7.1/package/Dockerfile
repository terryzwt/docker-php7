FROM zterry95/docker-php7:7.1-base

# Install Memcached
RUN curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/php7.tar.gz" && \
mkdir -p memcached && \
tar -C memcached -zxvf /tmp/memcached.tar.gz --strip 1 && \
( \
    cd memcached && \
    phpize && \
    ./configure && \
    make -j$(nproc) && \
    make install \
) && \
rm -r memcached && \
rm /tmp/memcached.tar.gz && \
docker-php-ext-enable memcached

# Install redis
RUN pecl install redis && docker-php-ext-enable redis

# Install xdebug
RUN pecl install xdebug && docker-php-ext-enable xdebug

# Install php-profiler-extension
RUN curl -L -o /tmp/php-profiler-extension.tar.gz "https://github.com/tideways/php-profiler-extension/archive/master.tar.gz" && \
mkdir -p php-profiler-extension && \
tar -C php-profiler-extension -zxvf /tmp/php-profiler-extension.tar.gz --strip 1 && \
( \
    cd php-profiler-extension && \
    phpize && \
    ./configure && \
    make && make install \
) && \
rm -r php-profiler-extension && \
rm /tmp/php-profiler-extension.tar.gz && \
docker-php-ext-enable tideways 

VOLUME /app/web
WORKDIR /app/web
