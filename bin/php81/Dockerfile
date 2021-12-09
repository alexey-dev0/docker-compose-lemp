FROM php:8.1-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
	curl \
	wget \
	git \
	autoconf \
	build-essential \
	apt-utils \
	zlib1g-dev \
	libzip-dev \
	unzip \
	zip \
	libmagick++-dev \
	libmagickwand-dev \
	libpq-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpng-dev \
	libwebp-dev \
	libxpm-dev

RUN docker-php-ext-configure gd --with-jpeg --with-freetype

# Extensions
RUN docker-php-ext-install gd intl pdo_mysql mysqli zip sockets

# Xdebug
RUN pecl install xdebug && docker-php-ext-enable xdebug

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Clear package lists
RUN apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Permissions
RUN chown -R root:www-data /var/www/html
RUN chmod u+rwx,g+rx,o+rx /var/www/html
RUN find /var/www/html -type d -exec chmod u+rwx,g+rx,o+rx {} +
RUN find /var/www/html -type f -exec chmod u+rw,g+rw,o+r {} +

WORKDIR /var/www/html

EXPOSE 80
EXPOSE 443