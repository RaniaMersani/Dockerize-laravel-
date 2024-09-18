# Utiliser l'image PHP
FROM php:8.1-fpm

# Installer les dépendances système
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

# Nettoyer le cache d'apt
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Installer les extensions PHP
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Copier Composer depuis une image officielle
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Changer de répertoire de travail
WORKDIR /var/www/html

# Copier les fichiers de l'application dans le conteneur
COPY ./application /var/www/html

# Exécuter "composer install" pour installer les dépendances
RUN composer install --no-dev --optimize-autoloader
