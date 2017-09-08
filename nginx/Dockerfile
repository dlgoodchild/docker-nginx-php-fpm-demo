FROM nginx:1.13.5-alpine

RUN rm -rf /etc/nginx/sites-enabled && mv /etc/nginx/conf.d /etc/nginx/original.conf.d

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
