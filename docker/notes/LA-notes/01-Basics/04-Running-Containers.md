# Running our existing containers

- Till now we've pulled the images before running them. But without pulling them we can run those but it does the same as ***pull+run***

- If we want to connect to the containers which are running then we need to mention that while running the image. We need to run it in ***interactive*** mode and need to attach it to out terminal with the shell we want to use.

```
# docker run -it centos:centos6 /bin/bash
```

- By default you will be logged in to the root user to this container.
- When we come out of the container then it will not exist. Because we are running ***/bin/bash*** as the command and if once we are out of that then the container won't exist.
- Also we can run the containers in background as well which is through the ***disconnected*** mode.

```
# docker run -d centos:centos6 /bin/bash
```

- If we have a image from which we can run any application like a webserver or something then we can see the difference. When we start the webserver it will runs till we stop it.

> NOTE: SERVICES/DAEMONS WILL NOT BE RUN ON THE CONTAINERS. ANYTHING WHICH RUNS ON A CONTAINER IS AN APPLICATION, SO WE NEED TO SET THE DAEMON OFF TO RUN ANY APPLICATION WITHIN A CONTAINER

- If we want to exit the container which is running at current then we need to stop that either by using its name or by the CONTAINER ID.

```
# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
2e8cbb120796        centos:centos6      "/bin/bash"         3 minutes ago       Up 3 minutes                            goofy_colden  

# docker stop 2e8cbb120796 (or) docker stop goofy_colden
```

- We can also name the containers other than following the default names.

```
# docker run -it --name=CentOS1 centos:centos6 /bin/bash
# docker stop CentOS1
# docker rm -v CentOS1
```
