FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
  libzip-dev \
  libonig-dev \
  cron \
  libfreetype6-dev \
  libicu-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libxslt1-dev \
  zip \
  libpng-dev \
  libxml2-dev \
  libxslt-dev \
  libsodium-dev \
  git

RUN docker-php-ext-install \
  pdo \
  pdo_mysql \
  mysqli \
  sockets \
  bcmath \
  gd \
  intl \
  mbstring \
  opcache \
  pdo_mysql \
  soap \
  xsl \
  zip \
  calendar \
  fileinfo

RUN pecl install xdebug-2.9.5 \
    && docker-php-ext-enable xdebug

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer --version=1.10.26

WORKDIR /var/www

#Access Rights
ARG user_id=1000

CMD ["php-fpm"]