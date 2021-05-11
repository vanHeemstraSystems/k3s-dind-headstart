# 200 - Docker named networks

For more dynamic environments, you can also use k3s-dind with named Docker networks, such as a [bridge network](https://docs.docker.com/network/bridge/). Then, any other containers on the same named network with k3s-dind can access any Kubernetes services exposed by the k3s-dind cluster.

First, create a Docker network:

```
docker network create mynetwork
```

Then run k3s-dind attached to that network:

```
docker run -d --privileged --name k3s --hostname k3s --network mynetwork unboundedsystems/k3s-dind

# The second argument to get-kubeconfig.sh is the container name of k3s-dind
docker exec k3s get-kubeconfig.sh -yaml k3s > ./k3sconfig
```

Now, any container on ```mynetwork``` can access any service exposed by the k3s-dind cluster:

```
# Run a container that's on mynetwork and mount the kubeconfig
docker run --rm -it -v ${PWD}/k3sconfig:/k3sconfig --network mynetwork k3integrations/kubectl

# Now we're inside the container we just ran
export KUBECONFIG=/k3sconfig

kubectl get all
NAME             CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
svc/kubernetes   10.43.0.1    <none>        443/TCP   10m
```
