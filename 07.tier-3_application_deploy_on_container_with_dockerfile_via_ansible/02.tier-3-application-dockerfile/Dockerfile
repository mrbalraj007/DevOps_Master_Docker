# Use the official Ubuntu image as a base
FROM ubuntu:20.04

# Update the package list and install necessary packages
RUN apt-get update && apt-get install -y \
    nginx \
    php-fpm \
    php-mysql \
    mysql-server

# Copy the application code
COPY app /var/www/html/

# Expose port 80
EXPOSE 80

# Start the services
CMD service mysql start && service php7.4-fpm start && nginx -g 'daemon off;'
