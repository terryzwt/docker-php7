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

VOLUME /app/web
WORKDIR /app/web
