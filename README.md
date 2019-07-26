
# Apache + PHP5 Stack Using Docker

## Deprecated!!!
  - Not maintained anymore. Please see more advanced and newer stack [here](https://github.com/sohelaman/dockerized).

## Info
- Uses Debian Stretch image as the base.
- Default Apache vhost configuration is here: [apache2/vhosts/000-default.conf](apache2/vhosts/000-default.conf)
- Additional Apache configuration can be put here: [apache2/custom.conf](apache2/custom.conf)


## Build the image
- Download the repository, ```cd``` into it. Then run the following command to build the image.
```
# docker build -t dockerized-apache-php5 .
```

## Run the image
- Document root of the image is set to */var/www/html* directory and should not be changed.
- The following command will mount the */srv/http* directory in the host OS as the document root for the container. Do not forget to put the path of the directory you want to serve insead of */srv/http* directory.
```
# docker run -it -h docker-apache-php5 -v /srv/http:/var/www/html dockerized-apache-php5
```

## Multiple sites
- Same image can be used to serve multiple sites. In this case, multiple containers will run.
```
# docker run -it -h dockernode1 -v /srv/http/site1/public_html:/var/www/html dockerized-apache-php5
# docker run -it -h dockernode2 -v /srv/http/site2/public_html:/var/www/html dockerized-apache-php5
```

### Notes
- Docker host IP,
```
$ ip -4 addr show docker0 | grep -Po 'inet \K[\d.]+'
``` 
- Docker container IP,

From the host (lists all that are running),
```
# docker inspect -f '{{.Id}} - {{.Name}} - {{.NetworkSettings.IPAddress}}' $(docker ps -q)
```
From the container,
```
$ hostname -i
```
- A host file entry pointing to the container may sometimes come handy. For example, if the docker container IP is *172.17.0.2* then add the following line to the */etc/hosts* file of the host machine.
```
172.17.0.2	dockernode
``` 
