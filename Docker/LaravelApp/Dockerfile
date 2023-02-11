# Official PHP image as the base image
FROM php:7.4-fpm-alpine

# Official MySQL image as the database
FROM mysql:8.0

# Setting working directory
WORKDIR /app

# Copy the composer.json and composer.lock files to the container
COPY composer.json composer.lock ./

# Install dependencies with composer
RUN apk add --no-cache composer && composer install --no-dev --optimize-autoloader

# Copy the app code to the container
COPY . .

# Set the ownership of the app code to the www-data user and group
RUN chown -R www-data:www-data /app

# Run the PHP-FPM process as the www-data user
USER www-data

# Expose port 9000 for the PHP-FPM process
EXPOSE 5000

# Start the PHP-FPM process
CMD ["php-fpm"]
