FROM docker.io/nginxinc/nginx-unprivileged:latest

COPY html/ /usr/share/nginx/html/

USER root

RUN chown 1000730001:nginx -R /usr/share/nginx/html

USER ngnix