FROM caddy:2.4.3-alpine
RUN apk update \
&& apk upgrade \
&& apk add --no-cache php php-fpm php-phar php-fileinfo \
&& apk add --no-cache php-curl php-dom php-gd php-json php-mbstring php-openssl php-pdo_mysql php-tokenizer php-zip \
&& apk add composer \
&& composer create-project flarum/flarum . --stability=beta \
&& sed -i '13 c root * /srv/public'   /etc/caddy/Caddyfile \
&& sed -i '$ a php_fastcgi localhost:9000' /etc/caddy/Caddyfile \
&& echo -e "#!/bin/sh caddy run --config /etc/caddy/Caddyfile" > ./run.sh
CMD ["/bin/sh","./run.sh"]
