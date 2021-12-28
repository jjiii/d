FROM jekyll/jekyll:latest

RUM jekyll new . ; \

apk --no-cache add  caddy; \
mkdir -p  /etc/caddy;  \
wget -O /etc/caddy/Caddyfile "https://github.com/caddyserver/dist/raw/56302336e0bb7c8c5dff34cbcb1d833791478226/config/Caddyfile"; \

caddy run --config /etc/caddy/Caddyfile; \
