# Use a smaller base image
FROM php:8.2.11-fpm

# Install required packages
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        apt-utils \
        nano \
        wget \
        dialog \
        vim \
        git \
        curl \
        zlib1g-dev \
        libzip-dev \
        zip \
        libbz2-dev \
        locales \
        libicu-dev \
        libonig-dev \
        libxml2-dev \
        libcurl4-openssl-dev \
        libpq-dev \
        postgresql-client \
    && rm -rf /var/lib/apt/lists/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install required PHP extensions
RUN docker-php-ext-install pdo pdo_mysql pdo_pgsql zip bz2 intl mbstring curl xml

# Set the working directory
WORKDIR /var/www/html

# Expose port 5173
EXPOSE 5173

# Define the entry point
CMD ["php", "-S", "0.0.0.0:5173", "-t", "/var/www/html/public"]
