FROM alpine:3

WORKDIR ../digram
  
RUN apk update && \
  apk add --no-cache libxml2 libxml2-dev curl curl-dev autoconf $PHPIZE_DEPS && \
  apk add zlib-dev mariadb-client libzip-dev && \
  apk add freetype-dev libjpeg-turbo-dev libpng-dev tree && \
  docker-php-ext-install opcache mysqli pdo pdo_mysql xml mbstring curl session tokenizer json && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer    

#Remote Debug
#RUN echo 'zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20160303/xdebug.so"' >> /usr/local/etc/php/php.ini
#RUN echo 'xdebug.remote_enable=on' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.remote_autostart=on' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.remote_port=9001' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.remote_handler=dbgp' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.remote_connect_back=1' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.idekey=PHPSTROME' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#RUN echo 'xdebug.remote_host=localhost' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

#install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer



#RUN sed -i -e 's/listen.*/listen = 0.0.0.0:9000/' /usr/local/etc/php-fpm.conf

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]
