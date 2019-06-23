
# Apache + PHP5 stack using docker

## Build image

```
$ docker build -t dockerized-apache-php5 .
```

## Run image
```
$ docker run -it -v /srv/http:/var/www/html dockerized-apache-php5
```

### Notes
* Add an entry to /etc/hosts file of the host machine pointing the docker container
