FROM php:7.0-fpm

MAINTAINER David Garcia <me@davidgarcia.cat>

# Download and install Composer
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Install dependencies
# ~~~~~~~~~~~~~~~~~~~~

RUN apt-get update
RUN apt-get install -y openssl git unzip iputils-ping telnet

# Enable PHP ZIP Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~

RUN apt-get install -y zip unzip zlib1g-dev
RUN docker-php-ext-install zip

# Enable PHP OPCache Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN docker-php-ext-install opcache

# Enable PHP Redis Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~

#RUN pecl install -o -f redis
#RUN docker-php-ext-enable redis

# Enable PHP iRedis Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~

#RUN apt-get install -y libhiredis-dev
#RUN git clone https://github.com/nrk/phpiredis.git

#RUN cd phpiredis && phpize
#RUN cd phpiredis && ./configure --enable-phpiredis
#RUN cd phpiredis && make
#RUN cd phpiredis && make install

#RUN echo "[iredis]" > /usr/local/etc/php/conf.d/docker-php-ext-iredis.ini
#RUN echo "extension=phpiredis.so" >> /usr/local/etc/php/conf.d/docker-php-ext-iredis.ini

# Enable PHP XDebug Extension
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~

RUN pecl install xdebug

RUN docker-php-ext-enable xdebug

RUN echo "error_reporting = E_ALL" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "display_startup_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "display_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.idekey=\"PHPSTORM\"" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.remote_port=9001" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
