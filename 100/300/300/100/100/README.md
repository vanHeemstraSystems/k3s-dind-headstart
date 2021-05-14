# 100 - Creating a cluster with k3d purely from a config file (recommended)

Use the previously created k3s config file to create a cluster with k3d:

```
$ export KUBECONFIG=./k3sconfig
$ k3d create --config $KUBECONFIG
```

Check if the cluster has been created:

```
$ k3d cluster list
```
