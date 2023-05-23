FROM debian:buster


RUN apt-get update && apt-get install -y \
    php7.3-fpm \
    php7.3-mysql \
    php7.3-curl \
    php7.3-gd \
    php7.3-intl \
    php7.3-mbstring \
    php7.3-soap \
    php7.3-xml \
    php7.3-xmlrpc \
    php7.3-zip \
    wget

RUN mkdir -p /var/run/php && chmod 777 /var/run/php

WORKDIR /var/www/html

RUN wget https://ko.wordpress.org/wordpress-6.1.1-ko_KR.tar.gz \
    && tar xzf wordpress-6.1.1-ko_KR.tar.gz \
    && mv wordpress/* . \
    && rm wordpress-6.1.1-ko_KR.tar.gz

COPY ./conf/wp-config.php /var/www/html/wp-config.php

COPY ./conf/setup.sh /var/www

EXPOSE 9000

CMD bash /var/www/setup.sh