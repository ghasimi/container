# container
About container, docker, etc.

## Docker

Frequently used commands:

```bash
# list of images
docker images

# list of all containers
docker ps -a

# pull ubuntu with tag 22.04
docker pull ubuntu:22.04

# run a container from an image.
# run = create + start
# bind local port 5000 to container's port 80 
docker run -d -t -p 5000:80 --name myubuntu1 ubuntu:22.04

# stop a container
docker stop myubuntu1

# start a container
docker start myubuntu1

# bash on the container
docker exec -it myubuntu1 bash

# delete conainer (must be stopped first)
docker rm [hash of the conainer, e.g. from docker ps]

# delete an image
docker rmi [hash of the image, e.g. from docker images]

# construct a new image from the current container
docker commit container1 container2

```

### Dockerfile

Sample dockerfile to create a linux box and run a Flask app. Save this file in the project folder. Add a `.dockerignore` file to excludes files not needed in the image, similar to `.gitignore`. This particular file uses the default flask server, and is not recommened for production. 

```dockerfile
FROM ubuntu:22.04

WORKDIR /app

COPY . .

RUN apt update  && \
    apt install -y wget lsof python3.10 python3-pip python3-venv && \
    apt clean && \
    python3 -m venv .venv && \ 
    . ./.venv/bin/activate && \
    python3 -m pip install --upgrade pip && \
    pip3 install -r requirements.txt && \

CMD ["python3", "-m", "app"]

EXPOSE 80
```

To build the image:
```
docker build myimage:mytag .
```
