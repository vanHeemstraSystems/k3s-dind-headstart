# 500 - Changing k3s API server port

There are situations where you prefer to use port other than 8443 for k3s API server. For example, you want port 8443 to get ingress traffic, and to use port 6000 (for example) as the "Kubernetes API port". In this case you can use the ```K3S_API_PORT``` environment variable like this:

```
docker run -d --privileged --name k3s --hostname k3s -p 8443:8443 -p 6000:6000 -e K3S_API_PORT=6000 unboundedsystems/k3s-dind
```
