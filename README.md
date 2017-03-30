### setup

set up dns for the domain you want to use

generate letsencrypt certs

```docker run -it --rm -v /etc/letsencrypt:/etc/letsencrypt  -p 80:80 -p 443:443  xataz/letsencrypt  certonly --standalone  --agree-tos -m me@galp.co.uk -d pod.galp.co.uk```

```DIASPORA_HOST=pod.galp.co.uk POSTGRES_PASSWORD=mysecretepass docker-compose up # use -d to background``` 

#### create database if it does not exist (warning : it will wipe existing)

```docker-compose exec sh
RAILS_ENV=production bin/rake db:create db:schema:load
```



#### renew cert
add to cron (needs some hackery to use the nginx webroot
 docker run -it --rm -v /etc/letsencrypt:/etc/letsencrypt  -p 80:80 -p 443:443  xataz/letsencrypt renewal
