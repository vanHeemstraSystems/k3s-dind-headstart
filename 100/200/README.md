# 200 - Using Docker CLI

```
docker run -d --privileged --name k3s --hostname k3s -p 8443:8443 -e K3S_API_PORT=8443 unboundedsystems/k3s-dind
docker exec k3s get-kubeconfig.sh > ./k3sconfig
export KUBECONFIG=./k3sconfig

kubectl get nodes
NAME      STATUS    ROLES     AGE       VERSION
k3s       Ready     master    1m        v1.18.4+k3s1

kubectl create ...
```
