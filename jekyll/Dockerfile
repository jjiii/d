FROM jekyll/jekyll:latest

RUN apk  --no-cache add  caddy; \
mkdir -p  /etc/caddy;  \
wget -O /etc/caddy/Caddyfile "https://github.com/jjiii/dockerfile/blob/main/jekyll/Caddyfile"
RUN echo -e "#!/bin/sh\ncaddy run --config /etc/caddy/Caddyfile" > /script.sh
#jekyll new . ; \
#jekyll build; 



EXPOSE 80
EXPOSE 443
EXPOSE 2019
CMD [ "sh", "/script.sh" ]

#RUN echo -e "#!/bin/sh\ncaddy run --config /etc/caddy/Caddyfile" > /script.sh
#ENTRYPOINT ["/script.sh"]
#CMD [ "bash", "/script.sh" ]
#没括号是以shell模式运行(可使用环境变量)，推荐使用exec模式
#CMD /script.sh

