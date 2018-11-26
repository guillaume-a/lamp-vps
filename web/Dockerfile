FROM php:7.1-apache

RUN apt-get update -y && apt-get install -y libpng-dev

# PHP extensions
RUN docker-php-ext-install pdo pdo_mysql mysqli
RUN docker-php-ext-install gd

# Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');"

# SSH
RUN a2enmod rewrite ssl headers
RUN service apache2 restart

# CERTBOT
RUN echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" >> /etc/apt/sources.list.d/docker.list
RUN apt-get update -y && apt-get install python-certbot-apache -t stretch-backports

# NODE / NPM
#RUN apt-get install -y wget
#RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
#RUN nvm ls-remote
#RUN nvm install 10.13.0
