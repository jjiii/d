FROM php:8.0.12-fpm-alpine3.13
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions @composer  exif gd zip pdo_mysql 

RUN apk add  caddy;  \
mkdir -p  /etc/caddy;  \
wget -O /etc/caddy/Caddyfile "https://github.com/caddyserver/dist/raw/56302336e0bb7c8c5dff34cbcb1d833791478226/config/Caddyfile"; \
sed -i '13 c root * /flarum/public'   /etc/caddy/Caddyfile;  \
sed -i '$ a php_fastcgi localhost:9000' /etc/caddy/Caddyfile; \
mkdir -p  /flarum; \
chmod 777  /flarum 

WORKDIR /flarum
RUN composer create-project flarum/flarum  /flarum  --stability=beta;  \
composer require flarum-lang/chinese-simplified; \
composer require fof/upload; \
composer require league/flysystem-aws-s3-v3:1.*;  \
composer require zequeen/acgembed-remastered; \
composer require fof/pretty-mail; \
composer require fof/links; \
composer require v17development/flarum-seo;  \
composer require ganuonglachanh/sonic;  \
composer require afrux/forum-widgets-bundle:"*";  \
composer require justoverclock/hot-discussions:"*";  \
composer require itnt/flarum-uitab

WORKDIR /var/www/html
RUN echo -e "#!/bin/sh \nphp-fpm & \ncaddy run --config /etc/caddy/Caddyfile" > ./run.sh 
EXPOSE 80
EXPOSE 443
EXPOSE 2019
CMD ["/bin/sh","./run.sh"]