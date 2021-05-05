# 300 - Using docker-compose


## 100 - Dockerfile

Create a Dockerfile as follows:

```
FROM unboundedsystems/k3s-dind
```
containers/k3s-dind/Dockerfile

## 200 - sample.docker-compose.yml

Create a sample.docker-compose.yml as follows:

```
version: '3.7'

services:
  k3s-dind:
    build: .
    container_name: "k3s"
    hostname: "k3s" 
    privileged: true
    ports:
    - 8443:8443
```
containers/k3s-dind/sample.docker-compose.yml

Build and run the container:

```
$ cd containers/k3s-dind/
$ docker-compose up -d
```

Followed by these commands:

```
$ cd containers/k3s-dind/
$ docker exec k3s get-kubeconfig.sh > ./k3sconfig
```

Allow for some waiting, as this will take time ... A new file 'k3sconfig' will have been created in your current directory.

```
$ ls -la
k3sconfig
```
Next run these commands:

```
$ export KUBECONFIG=./k3sconfig

$ kubectl get nodes
NAME      STATUS    ROLES     AGE       VERSION
k3s       Ready     <none>    1m        v1.14.1-k3s.4
```
