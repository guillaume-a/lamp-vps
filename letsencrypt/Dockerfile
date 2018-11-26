FROM debian:jessie-backports

RUN apt-get update \
  && apt-get install -y letsencrypt -t jessie-backports \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /etc/letsencrypt/live/codr.fr \
  && openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/letsencrypt/live/codr.fr/privkey.pem \
    -out /etc/letsencrypt/live/codr.fr/fullchain.pem \
    -subj /CN=codr.fr
