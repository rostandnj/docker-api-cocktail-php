FROM alpine:latest

ADD https://dl.bintray.com/php-alpine/key/php-alpine.rsa.pub /etc/apk/keys/php-alpine.rsa.pub

RUN apk --update add ca-certificates && \
    echo "https://dl.bintray.com/php-alpine/v3.11/php-7.3" >> /etc/apk/repositories

# install php and some extensions
RUN apk add --update \
    coreutils \
    php \
    php-bz2 \
    php-json \
    php7-fpm \
    php7-apcu \
    php7-ctype \
    php7-curl \
    php7-dom \
    php7-iconv \
    php7-json \
    php7-intl \
    php7-mcrypt \
    php7-fileinfo\
    php7-mbstring \
    php7-opcache \
    php7-openssl \
    php7-pdo \
    php7-pdo_mysql \
    php7-mysqli \
    php7-xml \
    php7-session \
    php7-xdebug \
    php7-zip \
    php-redis \
    curl



COPY app.ini /etc/php7/conf.d/
COPY app.ini /etc/php7/cli/conf.d/
COPY xdebug.ini  /etc/php7/conf.d/

COPY app.pool.conf /etc/php7/php-fpm.d/
ADD start.sh /
RUN chmod 777 /start.sh

CMD ["sh","/start.sh"]

WORKDIR /var/www/testApi
EXPOSE 9001
