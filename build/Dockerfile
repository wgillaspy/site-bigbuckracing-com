FROM docker.io/nginxinc/nginx-unprivileged:latest

COPY html/ /usr/share/nginx/html/

USER root

RUN chown nginx:nginx -R /usr/share/nginx/html

USER ngnix