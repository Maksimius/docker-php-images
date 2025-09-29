FROM php:8.4-fpm

#locales
RUN apt-get update && apt-get install -y locales && \
    echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "uk_UA.UTF-8 UTF-8" >> /etc/locale.gen && \
    echo "ru_RU.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen

#ENV
ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV COMPOSER_ALLOW_SUPERUSER=1

#add Git
RUN apt-get -y install git mc nano

#Install fresh certs
RUN apt-get install -y --no-install-recommends ca-certificates && update-ca-certificates

#ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

# Install php extensions
# Default just in case
#RUN docker-php-ext-install -j$(nproc) iconv mbstring
# Others
RUN install-php-extensions gd mysqli pdo_mysql redis bcmath imagick gmp intl zip soap

#RUN pecl install imap

# Copy php configuratuins
COPY ./php/uploads.ini /usr/local/etc/php/conf.d/uploads.ini

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN composer config --global github-protocols https

# Очистка кеша
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

