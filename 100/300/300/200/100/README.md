# 100 - Creating a cluster with kubectl purely from a config file (recommended)

```
$ export KUBECONFIG = ./k3sconfig
$ kubectl create --config $KUBECONFIG
```

Check if the cluster has been created:

```
$ kubectl cluster list
```
