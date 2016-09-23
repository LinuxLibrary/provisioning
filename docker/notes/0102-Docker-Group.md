# Create a Docker group

The docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket
is owned by the user root and other users can access it with sudo. For this reason, docker
daemon always runs as the root user.

To avoid having to use sudo when you use the docker command, create a Unix group called doc
-ker and add users to it. When the docker daemon starts, it makes the ownership of the Unix
socket read/writable by the docker group.

To create the docker group and add your user:

- Create the docker group.
```
$ sudo groupadd docker
```
- Add your user to docker group.
```
$ sudo usermod -aG docker $USER
```
- Log out and log back in.
  This ensures your user is running with the correct permissions.

- Verify your work by running docker without sudo.
```
$ docker run hello-world
```
If this fails with a message similar to this:

> Cannot connect to the Docker daemon. Is 'docker daemon' running on this host?

Check that the DOCKER_HOST environment variable is not set for your shell. If it is, unset it.
