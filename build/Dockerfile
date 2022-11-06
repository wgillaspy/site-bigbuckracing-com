FROM docker.io/nginx:latest

COPY html/ /usr/share/nginx/html/

USER root

RUN chown nginx:nginx -R /usr/share/nginx/html

USER ngnix