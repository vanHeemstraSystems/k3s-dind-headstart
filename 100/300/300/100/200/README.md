# 200 - Creating a cluster with k3d with command line flags

Look at the help page on k3d create:

```
$ k3d create --help
```

```
$ K3S_CLUSTER_NAME='mycluster'
$ K3S_CLUSTER_FLAGS=''
$ k3d create $K3S_CLUSTER_NAME $K3S_CLUSTER_FLAGS
```

Check if the cluster has been created:

```
$ k3d cluster list
```
