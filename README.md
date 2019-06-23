
# Dockerized

## Build an image
- Download a docker file and build it (note the image name),
```
$ docker build -t <image-name> .
```

## Run an image
- Use the image name provided in the provided in the previous step to run it,
```
$ docker run -it <image-name>
```

- To mount a directory of the host to the docker node, pass the volume info.
- For example, mount */srv/http* of the host machine as */var/www/html* inside the docker node.
```
$ docker run -it -v /srv/http:/var/www/html <image-name>
```
