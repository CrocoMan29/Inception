# Pull our base image
FROM debian:bullseye

# Install nginx
RUN apt-get update -y && apt-get upgrade -y \
    && apt-get install -y nginx openssl

RUN mkdir -p /etc/nginx/ssl

RUN openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
       -out /etc/nginx/ssl/yismaail.crt \
       -keyout /etc/nginx/ssl/yismaail.key \
       -subj "/C=FR/ST=BENGUERIR/L=BENGUERIR/O=42 School/OU=yismaail/CN=yismaail/"

# Copy our nginx config file to conf.d folder inside the container
COPY conf/nginx.conf /etc/nginx/conf.d

# Run nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]