# Docker Image and Container Management

- We may be working around with many docker images and containers.
- Once the container has stopped then it will go to ***Exited*** status and those containers will remain as is.
- Also we'll be working with number of images and we might not need all of those.
- Depending on our need we can have them as is or else we need to remove those.
- To remove a container which is not running we need to use ***docker rm***

```
# docker rm <CONTAINER ID / NAME>
```

- To remove a docker image we need to use ***docker rmi***

```
# docker rmi <IMAGE-ID> / <REPOSITORY NAME with TAG>

Ex:

# docker rmi centos:centos6 (or)
# docker rmi 10611b26a8b9
```

- If we have containers running based on some images then we can't remove those. In case we want to remove then we have 2 choices
	- Stop the container if it is running and then remove it. Once the containers associated with that image were removed then we can remove the Images.

	```
	# docker ps -a | grep nginx:latest | awk '{print $1}' | xargs -r docker stop
	# docker ps -a | grep nginx:latest | awk '{print $1}' | xargs -r docker rm -v
	# docker images | grep 'nginx.*latest' | awk '{print $3}' | xargs -r docker rmi
	```

	- Else we can force the images to remove

	```
	# docker images | grep 'nginx.*latest' | awk '{print $3}' | xargs -r docker rmi -f
	```

- If we remove the images forcefully without removing the containers then the containers would exist on our machine and those can be used as that container would act like a clone copy of the base image.
- So if we have issue with the disk space then we can remove the images and can have the containers. Also we can pull the images as needed as those are less in size.
- The main advantage of these docker containers and images are we can have these running on our virtual environment with less resources too.
