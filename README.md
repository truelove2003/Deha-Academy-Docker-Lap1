# Deha Academy Docker Laravel Project

This is a Laravel project set up using Docker for development and deployment.

## Requirements

Before getting started, make sure you have the following installed on your local machine:

- Docker
- Docker Compose

## Installation

Follow these steps to get your development environment up and running:

### 1. Clone the repository:
   git clone https://github.com/truelove2003/deha-academy-docker-lap.git

### 2. Build and Start the Container:

Run the following command to build and start the Docker containers:

    docker-compose up -d

### 3. Create a Laravel Project
Once the containers are up, execute the following command to create a new Laravel project inside the container:
    docker-compose exec php bash
    composer create-project laravel/laravel laravel
### 4. Configure Nginx
Ensure that the Nginx configuration file (nginx/default.conf) is correctly set up to serve your Laravel application. The root directive in Nginx should point to /var/www/laravel/public.

server {
    listen 80;
    server_name localhost;

    root /var/www/laravel/public;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass php:9000;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

    location ~ /\.ht {
        deny all;
    }
}

### 5. Run PHP applications

    Route::get('/test', function () {
        return 'Hello, World!';
    });

After setting up everything, open your browser and navigate to:

    http://localhost:5000/test

### 6.Use Laradock to create a Laravel running environment, change the configuration (port, PHP version) of Laradock

    http://localhost:5000
