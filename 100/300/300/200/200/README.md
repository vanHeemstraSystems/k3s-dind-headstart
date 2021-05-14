# 200 - Creating a cluster with kubectl with command line flags

Look at the help page on kubectl create:

```
$ kubectl create --help
```

Use the required flags as found in above help page to create a cluster with kubectl:

```
$ export K3S_CLUSTER_NAME='mycluster'
$ export K3S_CLUSTER_FLAGS=''
$ kubectl create $K3S_CLUSTER_NAME $K3S_CLUSTER_FLAGS
```

Check if the cluster has been created:

```
$ kubectl cluster list
```
