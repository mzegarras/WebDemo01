FROM nginx:stable

ENV TZ=America/Lima
RUN mkdir -p /data/www
ADD ./data/nginx.conf /etc/nginx/nginx.conf
#ADD ./data/dist/demo-web /data/www
ADD ./dist/demo-web /data/www
EXPOSE 8085

CMD ["nginx", "-g", "daemon off;"]
