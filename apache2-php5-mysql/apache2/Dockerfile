FROM ubuntu:14.04
MAINTAINER Juan Manuel <juanzaragoza@live.com.ar>

RUN apt-get update
RUN apt-get --yes --force-yes install apache2

RUN apt-get --yes --force-yes install php5 libapache2-mod-php5
RUN apt-get --yes --force-yes --fix-missing install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

RUN apt-get --yes --force-yes install curl
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    composer self-update

ADD vhost.conf /etc/apache2/sites-available/vhost.conf
RUN a2ensite vhost.conf

RUN mkdir /var/www/public

RUN service apache2 restart

EXPOSE 80

WORKDIR /var/www/public