# Redirection Ports and Volumes

- Whenever we have the docker containers running on our host with ports exposed depending on the applications within the docker container. 
- So in this case we need to connect to that application through the IP Address of the container but not through the host directly.
- But there is a way of having that application contacted through our host other than using the IP Address of the container.
- Through binding the ports of the applications running on the container we can have the application available through the host as well.
- For doing this we need to use ***-P*** option while running the container. This will allow us to bind the ports on the container with some random ports on the host between 32768 - 65000

```
# docker run -d --name=MyWeb1 -P nginx:latest
# docker inspect `docker ps | grep nginx | awk '{print $1}'` | python -c 'import json, sys; print json.load(sys.stdin)[0]["NetworkSettings"]["IPAddress"]'
# echo " 80 -> $(docker ps | grep nginx | awk -F: '{print $3}' | awk -F- '{print $1}')"
# elinks http://172.17.0.1
# elinks http://localhost:32769
```

- Now we can be able to connect to nginx on the container through the localhost by using the port
- We can also list out all the ports of the containers and to which ports those are being redirected to from the host.

```
# docker port MyWeb1 $CONTAINERPORT
443/tcp -> 0.0.0.0:32768
80/tcp -> 0.0.0.0:32769
```

- In the simillar way we can bind the ports on the container to some specific ports on the host

```
# docker run -d --name=MyWeb2 -p 80:80 nginx:latest
# docker port MyWeb2 $CONTAINERPORT
# elinks http://localhost
```

---

- Now let us see how to mount any directory from our localhost to our container.
- If we are going to have continuous changes to our application or configs which we are using on our container or else some of the files or data which are being changed continuously then it would be safe and easy to have them on the host on a directory and mounted it to the container while running.
- Once we have mounted a directory while running the container then it will directly have all the changed of the files or data of the directory mounted from the host on to the container.
- To mount a directory we need to use ***-v*** option and directory from the host to be mounted, remote directory on the container separated by a colon

```
# docker run -d -p 80:80 -v /var/www:/usr/share/nginx/html --name=MyWeb1 nginx:latest
```
