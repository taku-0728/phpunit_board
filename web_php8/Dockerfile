FROM php:8.0-apache

# composer
RUN cd /tmp && curl -sS https://getcomposer.org/installer | php \
    && mv ./composer.phar /usr/bin/composer

CMD ["httpd", "-D", ""FOREGROUND] 
