# 300 - Using docker-compose


## 100 - Dockerfile

Create a Dockerfile as follows:

```
FROM unboundedsystems/k3s-dind
```
containers/k3s-dind/Dockerfile

## 200 - sample.docker-compose.yml

Create a sample.docker-compose.yaml as follows:

```
version: '3.7'

services:
  k3s-dind:
    build: .
```
containers/k3s-dind/sample.docker-compose.yaml
