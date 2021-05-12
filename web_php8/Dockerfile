FROM php:8.0-apache
    # apacheのドキュメントルートの設定をapacheディレクトリ内の物に変更
    COPY ./apache/*.conf /etc/apache2/sites-enabled/

    # ServerNameをfqdnという新規ファイルに書き込む
    RUN echo "ServerName localhost" | tee /etc/apache2/conf-available/fqdn.conf
    # fqdnファイルの設定を有効化
    RUN a2enconf fqdn

    # Composer
    ARG composer_ver=2.0.8
    ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
    RUN chmod +x /usr/local/bin/install-php-extensions && sync \
    && install-php-extensions @composer-${composer_ver}

    # その他パッケージ、PHP拡張
    RUN apt-get update \
    # unzip (composer create-project で必要)
    && apt-get install -y unzip \
    # Vim
    && apt-get install -y vim \
    # mod_rewrite 有効化
    && a2enmod rewrite
