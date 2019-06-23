
# Apache + PHP5 Stack Using Docker

- Uses Debian Stretch images as base.
- Default apache vhost configuration is provided in the file [apache2/vhosts/000-default.conf](apache2/vhosts/000-default.conf)


## Build the image
- Download the [Dockerfile](Dockerfile) first. Then run the following command to build the image.
- Note that the *dockerized-apache-php5* is the name of the image; this can be anything.
```
# docker build -t dockerized-apache-php5 .
```

## Run the image
- Document root of the image is set to */var/www/html* directory and should not be changed.
- The following command will mount the */srv/http* directory in the host OS as the document root for the image.
```
# docker run -it -v /srv/http:/var/www/html dockerized-apache-php5
```

### Notes
Add an entry to the */etc/hosts* file of the host pointing the docker container.
