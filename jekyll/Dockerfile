FROM jekyll/jekyll:latest
COPY --from=caddy:2.4.6-alpine /usr/bin/caddy /usr/bin/caddy

ENV CADDY_HOME /usr/bin/caddy
ENV PATH $CADDY_HOME:$PATH

RUN mkdir -p  /etc/caddy; \
echo -e ":80 \\nroot * /srv/jekyll/_site\nfile_server \n}" > /etc/caddy/Caddyfile; \
jekyll new . ; \
jekyll build; 


EXPOSE 80
EXPOSE 443

CMD ["caddy", "run", "--config", "/etc/caddy/Caddyfile"]

#RUN echo -e "#!/bin/sh\ncaddy run --config /etc/caddy/Caddyfile" > /script.sh; \
#chmod +x /script.sh; \
#cat /script.sh
#RUN echo -e "#!/bin/sh\ncaddy run --config /etc/caddy/Caddyfile" > /script.sh
#ENTRYPOINT ["/script.sh"]
#CMD [ "bash", "/script.sh" ]
#没括号是以shell模式运行(可使用环境变量)，推荐使用exec模式
#CMD /script.sh
#CMD ["caddy", "run", "--config", "/etc/caddy/Caddyfile"]

