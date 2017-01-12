FROM FROM zterry95/docker-php7:7.1-base
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
# Install xhprof
RUN git clone https://github.com/tideways/php-profiler-extension.git && \
	cd php-profiler-extension && \
	phpize && ./configure && make && make install \
	rm -r ../php-profiler-extension

VOLUME /app/web
WORKDIR /app/web
