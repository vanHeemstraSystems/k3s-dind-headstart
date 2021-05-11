# 300 - Using docker-compose


## 100 - Dockerfile

Create a Dockerfile as follows:

```
FROM unboundedsystems/k3s-dind
```
containers/k3s-dind/Dockerfile

## 200 - sample.docker-compose.yml

Create a sample.docker-compose.yml as follows:

```
version: '3.7'

services:
  k3s-dind:
    build: .
    container_name: "k3s"
    hostname: "k3s" 
    privileged: true
    ports:
    - 8443:8443
```
containers/k3s-dind/sample.docker-compose.yml

Build and run the container:

```
$ cd containers/k3s-dind/
$ docker-compose up -d
```

Followed by these commands:

```
$ cd containers/k3s-dind/
$ docker exec k3s get-kubeconfig.sh > ./k3sconfig
```

Allow for some waiting (if it takes more than a minute, you will have too little CPU or memory, better choose a more powerful server!), as this will take time ... A new file 'k3sconfig' will have been created in your current directory.

***WARNING***: Change the newly created file's permissions as it is currently unsafe (group-wide readable, world-wide readable) as follows:

```
$ ls -la
-rw-rw-r--. 1 cloud_user cloud_user 1052 May  6 12:34 k3sconfig
$ chmod 600 k3sconfig
$ ls -la
-rw-------. 1 cloud_user cloud_user 1052 May  6 12:34 k3sconfig
```

Have a look inside k3sconfig:

```
$vi k3sconfig

apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUJXRENCL3FBREFnRUNBZ0VBTUFvR0NDcUdTTTQ5QkFNQ01DTXhJVEFmQmdOVkJBTU1HR3N6Y3kxelpYSjIKWlhJdFkyRkFNVFl5TURJeU5USTROREFlRncweU1UQTFNRFV4TkRNME5EUmFGdzB6TVRBMU1ETXhORE0wTkRSYQpNQ014SVRBZkJnTlZCQU1NR0dzemN5MXpaWEoyWlhJdFkyRkFNVFl5TURJeU5USTROREJaTUJNR0J5cUdTTTQ5CkFnRUdDQ3FHU000OUF3RUhBMElBQkh5OERmQWdzeWdUL2tRUkhVa1VWVkUwS0hpQlAvMjRzZHhTdGMrM2FpcTQKanNXb2pKUzdodDJxVDFOWFBsekxqYVV6cEcvalRRV3plenhUWEZBTS85ZWpJekFoTUE0R0ExVWREd0VCL3dRRQpBd0lDcERBUEJnTlZIUk1CQWY4RUJUQURBUUgvTUFvR0NDcUdTTTQ5QkFNQ0Ewa0FNRVlDSVFEcVF2TER2TVdyCjl2a1UzamZqWmwzeS9JTUpwNWF0OGl6TFdjUEoycktvNlFJaEFLekI3TzNyN1AzOWlnTUl3SktsS3RGL1U4YisKaUNaM3ROY0prZXFVZ1FjdwotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==
    server: https://127.0.0.1:8443
  name: default
contexts:
- context:
    cluster: default
    user: default
  name: default
current-context: default
kind: Config
preferences: {}
users:
- name: default
  user:
    password: 040673c0b4752a243f43aed8052afd94
    username: admin
```

Next run these commands:

```
$ export KUBECONFIG=./k3sconfig
```
See for the purpose and use of KUBECONFIG environment variable, https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig

```
$ kubectl get nodes
NAME      STATUS    ROLES     AGE       VERSION
k3s       Ready     master    1m        v1.18.4+k3s1
```

If the above command fails, try the following, explicitely pointing to the local k3sconfig file:

```
$ kubectl get nodes --kubeconfig ./k3sconfig
```
