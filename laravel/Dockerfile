# Use the official PHP image as the base image
FROM php:7.4-cli

# Set the working directory inside the container
WORKDIR /var/www

# Install system dependencies
RUN apt-get update && \ 
    apt-get install libzip-dev -y && \    
    apt-get install git -y && \    
    docker-php-ext-configure zip

# Install PHP extensions
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" 

RUN php composer.phar create-project --prefer-dist laravel/laravel laravel

ENTRYPOINT [ "php", "laravel/artisan", "serve" ]
CMD [ "--host=0.0.0.0" ]