# Docker Base Images

- To run the docker containers we need to have the base images. By using the ***docker run*** command we can run containers by using the base images.
- We can search the base images from the command line by using the keywords.

```
# docker search centos
```

- From this search we can get both ***OFFICIAL*** as well as all the ***PUBLIC REPOSITORIES*** which contains the search string.
- After getting the results we can pull the image which we need. For example I'm trying to get the very basic image ***hello-world***

```
# docker pull hello-world
latest: Pulling from hello-world

7a5a2d73abce: Pull Complete
Digest: sha256:7820f4620e6cf3e795643fac2f6b09e7fd0a29e7e5c4eee6aac9ba0bedca158c
Status: Downloaded newer image for hello-world:latest
```

- Let us list out the images once

```
# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
hello-world         latest              7a5a2d73abce        2 weeks ago         1.84 kB
```

- Now after getting an image we need to run it. The best practice would be running the image with its name and tag.

```
# docker run hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```

> WE CAN RUN THE CONTAINERS ALSO WITH THE IMAGE ID AS WELL AND IT WILL ALSO DOES THE SAME.

- Now let us get the ***centos*** image. If we don't mention the tag by default it will pull the latest version of the image. But if we want a specific version then we need to mention the tag of the image.

```
# docker pull centos:centos6
centos6: Pulling from centos
3690474eb5b4: Pull complete
c40f84131ae5: Pull complete
c3bd2182e0b9: Pull complete
10611b26a8b9: Pull complete
Digest: sha256:25c9860b98433bed7d8fc38dce059d7ccec7649371004705651a7d7c371f332b
Status: Downloaded newer image for centos:centos6

```

- After pulling any image if we want to know the information about the container then we need to run ***docker inspect*** on that image id which would give us a ***json*** formatted output.

```
# docker inspect `docker images | grep hello | awk '{print $3}'`
```
