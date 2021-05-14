# 100 - Creating a cluster with kubectl purely from a config file (recommended)

```
$ K3S_CONFIG_FILE = ./k3sconfig
$ kubectl create --config $K3S_CONFIG_FILE
```

Check if the cluster has been created:

```
$ kubectl cluster list
```
