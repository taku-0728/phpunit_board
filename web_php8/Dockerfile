FROM php:8.0-apache

# Composer
  ARG composer_ver=2.0.8
  ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
  RUN chmod +x /usr/local/bin/install-php-extensions && sync \
    && install-php-extensions @composer-${composer_ver}

RUN apt-get update \
    # unzip (composer create-project で必要)
    && apt-get install -y unzip \
    # Vim
    && apt-get install -y vim \
    && a2enmod rewrite
