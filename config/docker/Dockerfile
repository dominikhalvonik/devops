FROM library/php:8.2.2-fpm

RUN docker-php-ext-install pdo pdo_mysql opcache

RUN apt update && \
    apt-get install -y git && \
    apt-get install -y libzip-dev && \
    apt-get install -y zip unzip

RUN pecl install redis && \
    docker-php-ext-enable redis

RUN pecl install xdebug && \
    docker-php-ext-enable xdebug

WORKDIR /var/www/app
COPY ./src ./
RUN chmod -R 777 uploads

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

EXPOSE 9000

CMD /bin/bash -c "php-fpm"