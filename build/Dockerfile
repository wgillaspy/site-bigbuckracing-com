FROM docker.io/nginxinc/nginx-unprivileged:latest

COPY html/ /usr/share/nginx/html/

RUN chown nginx:nginx -R /usr/share/nginx/html