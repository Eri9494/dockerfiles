FROM debian:buster

RUN apt-get update
RUN apt-get -y install \
    lsb-release \
    apt-transport-https \
    ca-certificates \
    wget \
    curl \
    git \
    unzip \
    nginx

RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php.list

ARG PHP_VERSION=7.4
RUN apt-get update && \
    apt-get -y install \
    php${PHP_VERSION} \
    php${PHP_VERSION}-dev \
    php${PHP_VERSION}-cli \
    php${PHP_VERSION}-fpm \
    php${PHP_VERSION}-psr \
    php${PHP_VERSION}-mbstring \
    php${PHP_VERSION}-bcmath \
    php${PHP_VERSION}-bz2 \
    php${PHP_VERSION}-intl \
    php${PHP_VERSION}-gd \
    php${PHP_VERSION}-mbstring \
    php${PHP_VERSION}-mysql \
    php${PHP_VERSION}-curl \
    php${PHP_VERSION}-zip

RUN rm /etc/alternatives/php && ln -s /usr/bin/php${PHP_VERSION} /etc/alternatives/php

RUN curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | bash
RUN apt-get update && \
    apt-get install php${PHP_VERSION}-phalcon

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN php${PHP_VERSION} ./composer-setup.php --install-dir=/usr/local/bin --filename=composer