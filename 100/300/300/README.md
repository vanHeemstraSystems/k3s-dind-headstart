# 300 - Create a cluster

Now that you have installed k3s, create a k3s cluster by means of either k3d (recommended) or kubectl.

First, create a sample k3d config file, which will be used when creating clusters:

```
apiVersion: k3d.io/v1alpha2
kind: Simple
name: k3d-demo
servers: 3
agents: 2
kubeAPI:
  hostIP: "0.0.0.0"
  hostPort: "6443" # Kubernetes API via localhost:6443
image: rancher/k3s:v1.19.4-k3s1
volumes:
  - volume: /tmp:/tmp/somepath
    nodeFilters:
      - all
ports:
  - port: 8080:80 # http via localhost:8080
    nodeFilters:
      - loadbalancer
  - port: 0.0.0.0:8443:443 # https via localhost:8443
    nodeFilters:
      - loadbalancer
env:
  - envVar: bar=baz
    nodeFilters:
      - all
labels:
  - label: foo=bar
    nodeFilters:
      - server[0]
      - loadbalancer

options:
  k3d:
    wait: true
    timeout: "360s"
    disableLoadbalancer: false
    disableImageVolume: false
  k3s:
    extraServerArgs:
      - --tls-san=127.0.0.1
    extraAgentArgs: []
  kubeconfig:
    updateDefaultKubeconfig: true
    switchCurrentContext: true
```
/containers/k3s-dind/sample.k3dconfig

Copy the content of ```sample.k3dconfig``` into a new ```k3dconfig``` file.

```
$ pwd
/containers/k3s-dind/
$ cp sample.k3dconfig k3dconfig
```

## 100 - Creating a cluster with k3d

See [README.md](./100/README.md)

## 200 - Creating a cluster with kubectl

See [README.md](./200/README.md)
