FROM phpdockerio/php7-fpm:latest

RUN apt-get update
RUN echo 'deb http://packages.dotdeb.org jessie all' > /etc/apt/sources.list.d/dotdeb.list
RUN apt-get -y --no-install-recommends install apt-transport-https
RUN curl http://www.dotdeb.org/dotdeb.gpg | apt-key add -
RUN apt-get update

# Install PHP
RUN apt-get -y --no-install-recommends install  php7.0-mbstring php7.0-memcached php7.0-mysql php7.0-redis php7.0-bcmath php7.0-bz2 php7.0-gd php7.0-imap php7.0-imagick php7.0-intl php7.0-ldap php7.0-soap php7.0-ssh2 php7.0-xmlrpc php7.0-xsl php7.0-xdebug

# Pimcore and Laravel Stuff
RUN apt-get -y --no-install-recommends install html2text ghostscript libreoffice pngcrush jpegoptim exiftool poppler-utils git wget


# Cleanup
RUN apt-get remove -y autoconf automake libtool nasm make pkg-config libz-dev build-essential g++ \
        && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


RUN echo "xdebug.idekey = PHPSTORM" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.default_enable = 1" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_enable = 1" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_autostart = 1" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_connect_back = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.profiler_enable = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_host = 127.0.0.1" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

COPY entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
CMD ["php-fpm"]
WORKDIR "/application"