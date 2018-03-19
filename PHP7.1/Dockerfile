FROM phpdockerio/php71-fpm:latest

# Install PHP
RUN apt-get update \
    && apt-get -y --no-install-recommends install  php-memcached php7.1-mbstring php7.1-mysql php-redis php7.1-bcmath php7.1-bz2 php7.1-gd php7.1-imap php-imagick php7.1-intl php7.1-ldap php7.1-soap php-ssh2 php7.1-xmlrpc php7.1-xsl php-yaml php-xhprof php-xdebug

# Pimcore Stuff
RUN apt-get -y --no-install-recommends install ffmpeg html2text ghostscript libreoffice pngcrush jpegoptim exiftool poppler-utils git wget

# Install Build Tools (getting removed later)
RUN apt-get -y --no-install-recommends install autoconf automake libtool nasm make pkg-config libz-dev build-essential g++

RUN cd ~

# Cleanup
RUN apt-get remove -y autoconf automake libtool nasm make pkg-config libz-dev build-essential g++ \
        && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


RUN echo "xdebug.idekey = PHPSTORM" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.default_enable = 1" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_enable = 1" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_autostart = 1" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_connect_back = 0" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.profiler_enable = 0" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini && \
    echo "xdebug.remote_host = 127.0.0.1" >> /etc/php/7.1/fpm/conf.d/20-xdebug.ini

COPY entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
CMD ["php-fpm"]
WORKDIR "/application"