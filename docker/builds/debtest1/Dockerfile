FROM debian:stable
MAINTAINER vmsnivas <vmsnivas@gmail.com>

RUN apt-get update && apt-get upgrade -y && apt-get install -y apache2 telnet elinks openssh-server

EXPOSE 80 22

CMD ["/usr/sbin/apache2ctl","-D","FOREGROUND"]
