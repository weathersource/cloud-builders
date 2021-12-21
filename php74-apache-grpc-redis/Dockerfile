FROM php:7.4-apache

# Update PHP Settings
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini" \
    && sed -E -i -e 's/max_execution_time = 0/max_execution_time = 120/' "$PHP_INI_DIR/php.ini" \
    && sed -E -i -e 's/memory_limit = 128M/memory_limit = 1024M/' "$PHP_INI_DIR/php.ini" \
    && sed -E -i -e 's/post_max_size = 8M/post_max_size = 64M/' "$PHP_INI_DIR/php.ini" \
    && sed -E -i -e "s/variables_order.*/variables_order = \"EGPCS\"/g" "$PHP_INI_DIR/php.ini"

# update apt-get
RUN apt-get update

# install composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# install redis
RUN pecl install redis-5.3.2 \
    && docker-php-ext-enable redis \
    && php -r "echo extension_loaded('redis') ? 'yes' : 'no';"

# install gRPC
RUN apt-get install -y -q git zlib1g-dev \ 
    && pecl install grpc-1.34.0 \
    && docker-php-ext-enable grpc \
    && php -r "echo extension_loaded('grpc') ? 'yes' : 'no';"

# install protobuf
RUN pecl install -of protobuf-3.14.0 \
    && docker-php-ext-enable protobuf \
    && php -r "echo extension_loaded('protobuf') ? 'yes' : 'no';"

# clear local repository of downloaded package files
RUN apt-get clean
RUN php -i
RUN a2enmod rewrite
