FROM maksimius/php-fpm-extended:8.4-fpm

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN install-php-extensions xdebug

# Copy php configuratuins
COPY ./php/uploads.ini /usr/local/etc/php/conf.d/uploads.ini
COPY ./php/xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

