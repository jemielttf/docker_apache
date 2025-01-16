FROM php:8.1-apache

RUN apt-get update && apt-get install -y git libzip-dev zip nano pdftk

RUN docker-php-ext-install zip

RUN curl -sSL https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 -o mhsendmail \
    && chmod +x mhsendmail \
    && mv mhsendmail /usr/local/bin/mhsendmail \
	&& echo 'sendmail_path = "/usr/local/bin/mhsendmail --smtp-addr=mailhog:1025"' > /usr/local/etc/php/conf.d/sendmail.ini

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer