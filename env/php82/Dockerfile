FROM php:8.2-fpm-alpine

WORKDIR /var/www/html

RUN apk update --no-cache \
&& apk add \
build-base \
freetype-dev \
libjpeg-turbo-dev \
libpng-dev \
libzip-dev \
zip \
jpegoptim optipng pngquant gifsicle \
icu-dev \
oniguruma-dev \
tzdata \
zlib-dev \
libpng-dev \
vim \
curl

RUN docker-php-ext-install intl pcntl mbstring pdo_mysql exif zip
RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/
RUN docker-php-ext-install gd

RUN rm -rf /var/cache/apk/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

ARG PORT=9000
ENV PORT 9000

CMD ["php-fpm"]
EXPOSE 9000
