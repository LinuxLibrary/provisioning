# Adjust memory and swap accounting

When users run Docker, they may see these messages when working with an image:
```
WARNING: Your kernel does not support cgroup swap limit. WARNING: Your
kernel does not support swap limit capabilities. Limitation discarded.
```

To prevent these messages, enable memory and swap accounting on your system. Enabling
memory and swap accounting does induce both a memory overhead and a performance degra
-dation even when Docker is not in use. The memory overhead is about 1% of the total 
available memory. The performance degradation is roughly 10%.

To enable memory and swap on system using GNU GRUB, do the following:

- Log into Ubuntu as a user with sudo privileges.
- Edit the /etc/default/grub file.
- Set the GRUB_CMDLINE_LINUX value as follows:
```
GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"
```
- Save and close the file.
- Update GRUB.
```
$ sudo update-grub
```
- Reboot your system.
