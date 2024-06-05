# Use Ubuntu 20.04 base image
FROM ubuntu:20.04

# Set environment variable to accept prompts
ENV DEBIAN_FRONTEND=noninteractive

# Disable checking for valid timestamps in apt
RUN echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99checkvalid

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    apache2 \
    mysql-server \
    php \
    && rm -rf /var/lib/apt/lists/*

# Expose ports
EXPOSE 80 443

# Start services
CMD service apache2 start && service mysql start && tail -f /dev/null

