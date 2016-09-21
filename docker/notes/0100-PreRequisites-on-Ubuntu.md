# PRE-REQUISITES FOR DOCKER INSTALLATION ON UBUNTU

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

- Next update package information, ensure that APT works with the https method, and that CA cer
  -tificates are installed.

 	- $ sudo apt-get update
	- $ sudo apt-get install apt-transport-https ca-certificates

- Add the new GPG key.

	- $ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

- Open the /etc/apt/sources.list.d/docker.list file in your favorite editor.
  If the file doesn’t exist, create it.

- Remove any existing entries. Add an entry for your Ubuntu operating system.
  The possible entries are:

- On Ubuntu Precise 12.04 (LTS)
  	- deb https://apt.dockerproject.org/repo ubuntu-precise main
- On Ubuntu Trusty 14.04 (LTS)
	- deb https://apt.dockerproject.org/repo ubuntu-trusty main
- On Ubuntu Wily 15.10
	- deb https://apt.dockerproject.org/repo ubuntu-wily main
- On Ubuntu Xenial 16.04 (LTS)
	- deb https://apt.dockerproject.org/repo ubuntu-xenial main

- Save and close the /etc/apt/sources.list.d/docker.list file.

- Update the APT package index.
	- $ sudo apt-get update

- Purge the old repo if it exists.
	- $ sudo apt-get purge lxc-docker

- Verify that APT is pulling from the right repository.
	- $ apt-cache policy docker-engine

From now on when you run apt-get upgrade, APT pulls from the new repository.

For Ubuntu Trusty, Wily, and Xenial, it’s recommended to install the linux-image-extra-* kernel packages.
The linux-image-extra-* packages allows you use the aufs storage driver.

To install the linux-image-extra-* packages:

- Update your package manager.
	- $ sudo apt-get update

- Install the recommended packages.
	- $ sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual

- Go ahead and install Docker.

Ubuntu Precise 12.04 (LTS)
For Ubuntu Precise, Docker requires the 3.13 kernel version. If your kernel version is older than 3.13,
you must upgrade it. Refer to this table to see which packages are required for your environment:

Package	Description
-------------------
linux-image-generic-lts-trusty | Generic Linux kernel image. This kernel has AUFS built in. This is required to run Docker.
---------------------------------|--------------------------------------------------------------
linux-headers-generic-lts-trusty | Allows packages such as ZFS and VirtualBox guest additions which depend on them. If you didn't install the headers for your existing kernel, then you can skip these headers for the"trust -y" kernel. If you're unsure, you should include this package for safety.
xserver-xorg-lts-trusty	| Optional in non-graphical environments without Unity/Xorg. Required when running Docker on machine with a graphical environment.
libgl1-mesa-glx-lts-trusty | To learn more about the reasons for these packages, read the installation instructions for backported kernels, specifically the LTS Enablement Stack — refer to note 5 under each version.

To upgrade your kernel and install the additional packages, do the following:

- Update your package manager.
	- $ sudo apt-get update

- Install both the required and optional packages.
	- $ sudo apt-get install linux-image-generic-lts-trusty

- Depending on your environment, you may install more as described in the preceding table.

- Reboot your host.
	- $ sudo reboot

- After your system reboots, go ahead and install Docker.
