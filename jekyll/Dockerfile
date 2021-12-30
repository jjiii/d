FROM jekyll/jekyll:latest

#RUN apk add  caddy; \
#mkdir -p  /etc/caddy;  \
#wget -O /etc/caddy/Caddyfile "https://github.com/jjiii/dockerfile/blob/main/jekyll/Caddyfile"; \
#jekyll new . ; \
#jekyll build; 

#WORKDIR /srv/jekyll
RUN echo -e "#!/bin/sh\necho '********************************************************'" > /script.sh && cat /script.sh 

RUN ["chmod", "+x", "/script.sh"]

EXPOSE 80
EXPOSE 443
EXPOSE 2019

ENTRYPOINT ["/script.sh"]


