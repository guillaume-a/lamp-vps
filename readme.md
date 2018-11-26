Source : https://devsidestory.com/lets-encrypt-with-docker/

Create cert

docker-compose run --rm letsencrypt \
  letsencrypt certonly --webroot \
  --email me@example.org --agree-tos \
  -w /var/www/letsencrypt -d my.example.org

  Renew cert

  docker-compose run --rm letsencrypt letsencrypt renew
