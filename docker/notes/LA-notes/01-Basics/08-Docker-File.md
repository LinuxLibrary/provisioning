# Working with Docker File

- Let us see how to create our own Docker Base Image.
- For example we need a container with some basic functionality.
- To build a docker image we need a docker file. So let us see how to write a docker file.
- We will have several keywords being used to write a docker file. Let us see what are those and how they works.

	- ***FROM***

	```
	FROM debian:stable

	This is the keyword used to tell docker where to look to build the image. In this case we are using "debian:stable".
	So we are looking into the "stable" version of "debian" repository from docker hub
	```

	- ***MAINTAINER***

	```
	MAINTAINER vmsnivas <vmsnivas@gmail.com>

	Docker account and email of the person who is going to maintain this. (We are using the docker hub account details)
	```

	- ***RUN***

	```
	RUN apt-get update
	
	This directive is used to run the commands and will be executed as root. Any command after this directive will be
	treated as the commands to be executed while building the image.
	```
	> While creating a docker file if we use multiple RUN directives then each of the operation will create a new container.
	> Which will occupy more space on our filesystem. To overcome this situation we need to combine the commands with as less
	> RUN directives as possible.

	```
	RUN apt-get update && apt-get upgrade -y && apt-get install -y apache2 telnet elinks openssh-server
	```

	- ***EXPOSE***

	```
	EXPOSE 80

	This directive is used to expose the ports on the container. If we want to use any application which is running on
	the container then we need to expose the concerning port of the application. If you want to expose more ports then
	you need to simply separate those with a white space.
	```
	
	- ***CMD***

	```
	CMD ["/usr/sbin/apache2ctl","-D","FOREGROUND"]
	
	This directive is used to run commands. But there is a main difference between RUN and CMD. RUN will execute a set of
	commands while creating an Image and CMD will execute commands on a container which has been created based upon that
	image. And here in the above example we are using "-D" option to run apache as application with DAEMON mode OFF
	```

- Now we need to build the docker image using the path of the docker file using ***docker build***

```
# docker build -t vmsnivas/debtest1 .
```


