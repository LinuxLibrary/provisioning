# Enable UFW forwarding

If you use UFW (Uncomplicated Firewall) on the same host as you run Docker, you’ll need to
do additional configuration. Docker uses a bridge to manage container networking. By defau
-lt, UFW drops all forwarding traffic. As a result, for Docker to run when UFW is enabled,
you must set UFW’s forwarding policy appropriately.

Also, UFW’s default set of rules denies all incoming traffic. If you want to reach your co
-ntainers from another host allow incoming connections on the Docker port. The Docker port
defaults to 2376 if TLS is enabled or 2375 when it is not. If TLS is not enabled, communic
-ation is unencrypted. By default, Docker runs without TLS enabled.

To configure UFW and allow incoming connections on the Docker port:

- Log into Ubuntu as a user with sudo privileges.
- Verify that UFW is installed and enabled.
```
$ sudo ufw status
```
- Open the /etc/default/ufw file for editing.
```
$ sudo nano /etc/default/ufw
```
- Set the DEFAULT_FORWARD_POLICY policy to:
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```
- Save and close the file.
- Reload UFW to use the new setting.
```
$ sudo ufw reload
```
- Allow incoming connections on the Docker port.
```
$ sudo ufw allow 2375/tcp
```
