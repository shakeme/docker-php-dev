FROM shakeme/php:apache

MAINTAINER Robert Schneider <shakemedev@gmail.com>

# install tools
RUN apt-get update \
    && apt-get install --assume-yes \
        ssmtp

# configure tools
RUN echo "hostname=localhost.localdomain" > /etc/ssmtp/ssmtp.conf \
    && echo "root=developer@localhost" >> /etc/ssmtp/ssmtp.conf \
    && echo "mailhub=mailhog:1025" >> /etc/ssmtp/ssmtp.conf \
    && echo "localhost localhost.localdomain" >> /etc/hosts

# install and enable extensions
RUN pecl install \
        xdebug \
    && docker-php-ext-enable \
        xdebug

# cleanup
RUN apt-get --assume-yes autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /tmp/*

