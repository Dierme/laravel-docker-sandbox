FROM php:7.4-fpm

# Set working directory
WORKDIR /var/www/laravel-demo

# Copy existing application directory contents
COPY . .


# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libzip-dev \
    openssl

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
#RUN docker-php-ext-install pdo_mysql mbstring zip exif pcntl
#RUN docker-php-ext-configure gd --with-gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/
#RUN docker-php-ext-install gd

RUN docker-php-ext-install pdo zip exif pcntl


# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer install

# Add user for laravel application
RUN groupadd -g 1000 app
RUN useradd -u 1000 -ms /bin/bash -g app app

# Copy existing application directory permissions
COPY --chown=app:app . /var/www/laravel-demo
RUN chmod 755 storage/logs

# Change current user to www
USER app

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]
