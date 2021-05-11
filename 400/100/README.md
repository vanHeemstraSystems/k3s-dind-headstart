# 100 - Docker host networking

The Quick Start example above uses Docker's [host networking](https://docs.docker.com/network/host/), using the ```-p 8443:8443``` option to ```docker run``` to expose the Kubernetes API port. To run Kubernetes [services](https://kubernetes.io/docs/concepts/services-networking/service/) and make them available outside the cluster, you would need to use additional ```-p``` options to ```docker run```, because Docker doesn't support exposing additional host networking ports after the container has been started.

For example, to allow your Docker host to connect to a [Kubernetes service running on port 8080](https://kubernetes.io/docs/tasks/access-application-cluster/service-access-application-cluster/), you'd need to start k3s-dind like this:

```
docker run -d --privileged --name k3s --hostname k3s -p 8443:8443 -p 8080:8080 unboundedsystems/k3s-dind
```
