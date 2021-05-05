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
# to run define K3S_TOKEN, K3S_VERSION is optional, eg:
#   K3S_TOKEN=${RANDOM}${RANDOM}${RANDOM} docker-compose up

version: '3.7'

services:
  k3s-dind-server:
    build: .
    command: server
    tmpfs:
    - /run
    - /var/run
    privileged: true
    environment:
    - K3S_TOKEN=${K3S_TOKEN:?err}
    - K3S_KUBECONFIG_OUTPUT=/output/kubeconfig.yaml
    - K3S_KUBECONFIG_MODE=666
    volumes:
    - k3s-server:/var/lib/rancher/k3s
    # This is just so that we get the kubeconfig file out
    - .:/output
    ports:
    - 6443:6443
    
  k3s-dind-agent:
    build: .
    tmpfs:
    - /run
    - /var/run
    privileged: true
    environment:
    - K3S_URL=https://server:6443
    - K3S_TOKEN=${K3S_TOKEN:?err}

volumes:
  k3s-server: {}
```
containers/k3s-dind/sample.docker-compose.yml
