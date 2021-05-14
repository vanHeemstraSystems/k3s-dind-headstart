# 100 - Creating a cluster with k3d

## 100 - Creating a cluster with k3d purely from a config file (recommended)

See [README.md](./100/README.md)

Use the previously created k3s config file to create a cluster with k3d:

```
$ K3S_CONFIG_FILE = ./k3sconfig
$ k3d create --config $K3S_CONFIG_FILE
```

Check if the cluster has been created:

```
$ k3d cluster list
```

## 200 - Creating a cluster with k3d with command line flags

See [README.md](./200/README.md)

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
