# 100 - Prerequisites

## 100 - Docker and docker-compose
- For installation of Docker, see https://github.com/vanHeemstraSystems/docker-quick-start-headstart

- For installation of docker-compose, see https://github.com/vanHeemstraSystems/docker-compose-quick-start-headstart

## 200 - Kubectl (Optional)
For installation of kubectl, see https://phoenixnap.com/kb/how-to-install-kubernetes-on-centos

## 300 - Disable SELinux
The Docker containers need to access the host filesystem. SELinux needs to be set to ***permissive*** mode, which effectively disables its security functions.

Use following commands to disable SELinux:

```
$ sudo setenforce 0
$ sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config
```

Check if it is now "Permissive", with:

```
$ getenforce
Permissive
```

All good!
