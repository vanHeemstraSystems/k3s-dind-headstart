# 100 - Creating a cluster with kubectl purely from a config file (recommended)

Uses the previously created k3d config file.

```
$ export K3D_CONFIG=./k3dconfig
$ kubectl create --config $K3D_CONFIG
```

Check if the cluster has been created:

```
$ kubectl cluster list
```
