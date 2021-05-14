# 100 - Creating a cluster with k3d purely from a config file (recommended)

Use the previously created k3d config file to create a cluster with k3d:

```
$ export K3D_CONFIG=./k3dconfig
$ k3d create --config $K3D_CONFIG
```

Check if the cluster has been created:

```
$ k3d cluster list
```
