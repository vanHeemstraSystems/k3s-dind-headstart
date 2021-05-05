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

Follow with these commands:

```
docker exec k3s get-kubeconfig.sh > ./k3sconfig
export KUBECONFIG=./k3sconfig

kubectl get nodes
NAME      STATUS    ROLES     AGE       VERSION
k3s       Ready     <none>    1m        v1.14.1-k3s.4
```
