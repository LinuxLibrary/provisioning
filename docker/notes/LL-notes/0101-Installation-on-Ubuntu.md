# DOCKER INSTALLATION ON UBUNTU

Docker is supported on these Ubuntu operating systems:

Ubuntu Xenial 16.04 (LTS)
Ubuntu Wily 15.10
Ubuntu Trusty 14.04 (LTS)
Ubuntu Precise 12.04 (LTS)

Prerequisites :
* Docker requires a 64-bit installation regardless of your Ubuntu version. Additionally, your
  kernel must be 3.10 at minimum. The latest 3.10 minor version or a newer maintained version
  are also acceptable.

* Kernels older than 3.10 lack some of the features required to run Docker containers. These 
  older versions are known to have bugs which cause data loss and frequently panic under cert
  -ain conditions.

* To check your current kernel version, open a terminal and use uname -r to display your kern
  -el version

DOCKER INSTALLATION :
---------------------

Make sure you have installed the prerequisites for your Ubuntu version.

Then, install Docker using the following:

- Update your APT package index.
	- $ sudo apt-get update

- Install Docker.
	- $ sudo apt-get install docker-engine

- Start the docker daemon.
	- $ sudo service docker start

- Verify docker is installed correctly.
	- $ sudo docker run hello-world

  This command downloads a test image and runs it in a container. When the container runs
  it prints an informational message. Then, it exits.
