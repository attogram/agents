# Use the latest Ubuntu LTS as a base image
FROM ubuntu:22.04

# Set non-interactive frontend for package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install common development tools and NGINX
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    git \
    curl \
    wget \
    nginx \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Copy the NGINX configuration file
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the static HTML content
COPY html/ /var/www/html/

# Expose port 80 for the web server
EXPOSE 80

# Start NGINX when the container launches
CMD ["nginx", "-g", "daemon off;"]
