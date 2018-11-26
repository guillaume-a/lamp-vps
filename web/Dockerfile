FROM php:7.1-apache

RUN apt-get update -y && apt-get install -y libpng-dev

# PHP extensions
RUN docker-php-ext-install pdo pdo_mysql mysqli
RUN docker-php-ext-install gd

# Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

# NODE / NPM
RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
RUN nvm ls-remote
RUN nvm install 10.13.0

# SSH
RUN a2enmod rewrite ssl headers
RUN service apache2 restart

# CERTBOT
RUN apt-get install python-certbot-apache -t stretch-backports
