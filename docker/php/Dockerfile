FROM php:8.3-fpm-alpine

# Dependencias del sistema + extensiones que Laravel necesita
RUN apk add --no-cache \
        git curl bash \
        libzip-dev zip unzip \
        libpng-dev libjpeg-turbo-dev freetype-dev \
        oniguruma-dev icu-dev \
    && docker-php-ext-configure gd --with-jpeg --with-freetype \
    && docker-php-ext-install -j"$(nproc)" \
        pdo_mysql mbstring exif pcntl bcmath gd zip intl

# Composer (copiado directo de la imagen oficial, sin instalar nada extra)
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

EXPOSE 9000
CMD ["php-fpm"]
