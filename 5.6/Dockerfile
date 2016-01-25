FROM php:5.6

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        zlib1g-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd zip \
    && apt-get clear

RUN curl https://get.docker.com/builds/Linux/x86_64/docker-latest -o /usr/local/bin/docker \
    && chmod +x /usr/local/bin/docker \
    && curl -L https://phar.phpunit.de/phpunit.phar -o /usr/local/bin/phpunit \
    && chmod +x /usr/local/bin/phpunit \
    && curl -sS https://getcomposer.org/installer -o /installer.php \
    && php /installer.php \
    && mv composer.phar /usr/local/bin/composer \
    && composer global require phpspec/phpspec \
    && ln -s /root/.composer/vendor/bin/phpspec /usr/local/bin/phpspec

