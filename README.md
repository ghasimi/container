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
docker stop myubuntu1

# delete conainer (must be stopped first)
docker rm [hash of the conainer, e.g. from docker ps]

# delete an image
docker rmi [hash of the image, e.g. from docker images]

```
