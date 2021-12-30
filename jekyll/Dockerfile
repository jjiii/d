FROM jekyll/jekyll:latest

RUN apk add  caddy; \
mkdir -p  /etc/caddy;  \
wget -O /etc/caddy/Caddyfile "https://github.com/jjiii/dockerfile/blob/main/jekyll/Caddyfile"; \
jekyll new . ; \
jekyll build; 

WORKDIR /srv/jekyll
RUN echo -e "caddy run --config /etc/caddy/Caddyfile" > ./run.sh && cat /srv/jekyll/run.sh 

EXPOSE 80
EXPOSE 443
EXPOSE 2019
CMD ["/bin/sh","./run.sh"]



