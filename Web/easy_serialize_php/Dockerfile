FROM php:7.0-apache
RUN buildDeps=" \
        default-libmysqlclient-dev \
        libbz2-dev \
        libmemcached-dev \
        libsasl2-dev \
    " \
    runtimeDeps=" \
        curl \
        git \
        libfreetype6-dev \
        libicu-dev \
        libjpeg-dev \
        libldap2-dev \
        libmcrypt-dev \
        libmemcachedutil2 \
        libpng-dev \
        libpq-dev \
        libxml2-dev \
    " \
    && apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y $buildDeps $runtimeDeps mysql-server \
    && docker-php-ext-install mysqli && docker-php-ext-install soap  
COPY www /var/www/html
COPY php.ini /usr/local/etc/php/php.ini
COPY ./run.sh /var/www/run.sh
RUN chmod +x /var/www/run.sh
WORKDIR /var/www/html
EXPOSE 80
