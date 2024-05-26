FROM php:7.4-cli

WORKDIR /var/www

# Atualizando debian e instalando a extensão ZIP
# docker-php-ext-install zip -> Peculiaridade dessa imagem do PHP para instalar facilmente extensões
RUN apt-get update && \
    apt-get install libzip-dev -y && \
    docker-php-ext-install zip

# Instalando Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');"

# Instalando laravel
RUN php composer.phar create-project laravel/laravel laravel

# ENTRYPOINT

ENTRYPOINT [ "php", "laravel/artisan", "serve" ]
CMD [ "--host=0.0.0.0" ]