FROM php:7.2-fpm

ENV XDEBUG_VERSION 2.6.0beta1

RUN apt-get update && \
    apt-get install -y git zip \
    zlib1g-dev libicu-dev libmcrypt-dev libbz2-dev libxslt-dev curl unzip wget && \
    pecl install apcu
RUN docker-php-ext-install -j$(nproc) mysqli intl bcmath zip bz2 mbstring pcntl xsl pdo pdo_mysql opcache
RUN docker-php-ext-enable apcu

RUN cd /tmp && \
  wget http://xdebug.org/files/xdebug-$XDEBUG_VERSION.tgz && \
  tar -xvzf xdebug-$XDEBUG_VERSION.tgz && \
  cd xdebug-$XDEBUG_VERSION && \
  phpize && \
  ./configure && \
  make && \
  make install && \
  rm -rf /tmp/xdebug-$XDEBUG_VERSION && \
  rm /tmp/xdebug-$XDEBUG_VERSION.tgz

RUN curl --silent --show-error https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY config/opcache.ini /usr/local/etc/php/conf.d/20-opcache.ini
COPY config/general.ini /usr/local/etc/php/conf.d/20-general.ini
COPY config/xdebug.ini /usr/local/etc/php/conf.d/20-xdebug.ini

RUN groupadd -g 1000 -o -f user && \
  useradd --shell /bin/bash -u 1000 -g user -o -c "" -m user

USER user

WORKDIR "/var/www"