# Docker Installation and Configuration

- Create a YUM repository for docker
```
	# cd /etc/yum.repos.d/
	# vi docker.repo
	
	[docker-repo]
	name=Docker Repository
	baseurl=https://yum.dockerproject.org/repo/main/centos/7/
	enabled=1
	gpgcheck=1
	gpgkey=https://yum.dockerproject/gpg

	# yum update
```

- Install Docker-Engine
```
	# yum install docker-engine -y
	# systemctl enable docker
	# systemctl start docker
```

- To check the docker images running on the system run the below command. It will not show any images as we don't have any images configured yet.
```
	# docker images
```

- docker.sock file located at /var/run is responsible for managing docker. This is the file which provides connections to docker. If we want normal users to manage docker we need to add the user to docker group. Only ***root*** and the users belong to ***docker*** group can manage docker.
