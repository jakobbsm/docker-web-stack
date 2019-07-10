FROM php:7.2-fpm

RUN apt-get update && apt-get install -y --fix-missing \
    apt-utils \
    gnupg \
    git \
    curl

RUN echo "deb http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list
RUN echo "deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list
RUN curl -sS --insecure https://www.dotdeb.org/dotdeb.gpg | apt-key add -

RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    libpng-dev \
    libicu-dev \
    libxml2-dev
RUN pecl install xdebug-2.7.2 \
	&& docker-php-ext-configure zip --with-libzip \
	&& docker-php-ext-install pdo_mysql mysqli zip gd intl xmlrpc soap opcache \
	&& docker-php-ext-enable xdebug

# MailHog
RUN curl -Lsf 'https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz' | tar -C '/usr/local' -xvzf -
ENV PATH /usr/local/go/bin:$PATH
RUN go get github.com/mailhog/mhsendmail
RUN cp /root/go/bin/mhsendmail /usr/bin/mhsendmail
# RUN echo 'sendmail_path = /usr/bin/mhsendmail --smtp-addr mailhog:1025' > /usr/local/etc/php/php.ini
