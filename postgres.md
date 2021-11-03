# Run Postgres using 3 replicas on specific nodes

Original helm repository: https://github.com/bitnami/charts/tree/master/bitnami/postgresql
### Enabling replication:
```yaml
replication:
  enabled: true
  readReplicas: 3
```
### Make it tolerate out taint:
```yaml
primary:
  tolerations:
    - key: db
    operator: Exists
```
In this case out taints created like this:
```yaml
$ kubectl taint no worker4-db db:NoSchedule
$ kubectl taint no worker5-db db:NoSchedule
$ kubectl taint no worker6-db db:NoSchedule
```
### Finally run:
```
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install my-release bitnami/postgresql -f postgres.yaml
```
