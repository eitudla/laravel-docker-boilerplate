FROM ubuntu:18.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
    apt-get install -y apache2 libapache2-mod-php \
    curl gnupg2 \
    php php-mysql php-intl php-opcache php-token-stream php-gd php-fpm \
    php-gd php-curl php-cli \
    php-imap php-json php-xml php-mbstring php-zip php-pdo \
    git htop vim cron mailutils && \
    a2enmod rewrite headers ssl deflate expires


COPY . /var/www/html

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html

RUN chown -R www-data:www-data \
        /var/www/html

RUN chgrp -R www-data storage bootstrap/cache && \
    chown -R www-data storage bootstrap/cache && \
    chmod -R ug+rwx storage bootstrap/cache && \
    touch storage/logs/laravel.log && chmod 775 storage/logs/laravel.log && chown www-data storage/logs/laravel.log

RUN cd /var/www/html && composer install && php artisan key:generate

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
