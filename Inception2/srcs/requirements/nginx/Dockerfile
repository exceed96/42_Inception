FROM debian:buster

RUN apt-get update && apt-get install -y nginx && apt-get install -y openssl


RUN mkdir /etc/nginx/ssl
RUN openssl req -x509 -nodes -days 365 \
    -subj "/C=KR/ST=Seoul/O=Company, Inc./CN=sangyeki.42.fr" \
    -addext "subjectAltName=DNS:sangyeki.42.fr" \
    -newkey rsa:2048 -keyout /etc/nginx/ssl/sangyeki.key \
    -out /etc/nginx/ssl/sangyeki.crt

# Copy nginx.conf
COPY ./conf/nginx.conf /etc/nginx/conf.d

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]