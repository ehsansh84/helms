# Run Postgres using 3 replicas on specific nodes

Original helm repository: https://github.com/bitnami/charts/tree/master/bitnami/postgresql
### Enabling replication:
```yaml
replication:
  enabled: true
  readReplicas: 3
```
### Make it tolerate our taint:
```yaml
primary:
  tolerations:
    - key: db
    operator: Exists
```
In this case our taints created like this:
```yaml
$ kubectl taint no worker4-db db:NoSchedule
$ kubectl taint no worker5-db db:NoSchedule
$ kubectl taint no worker6-db db:NoSchedule
```
### Finally run:
```
kubectl create namespace postgres
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install -n postgres postgres bitnami/postgresql -f values.yaml
```
You can acquire password this way:
```
export POSTGRES_PASSWORD=$(kubectl get secret -n postgres postgres-postgresql -o jsonpath="{.data.postgresql-password}" | base64 --decode)
```
Exec into database like this:
```commandline
kubectl run postgres-postgresql-client --rm --tty -i --restart='Never' -n postgres --image docker.io/bitnami/postgresql:11.14.0-debian-10-r0 --env="PGPASSWORD=$POSTGRES_PASSWORD" --command -- psql --host postgres-postgresql -U postgres -d postgres -p 5432
```
You can easily manage Postgres through a webgui:
```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: pgweb
  name: pgweb
spec:
  containers:
    - image: sosedoff/pgweb
      name: pgweb
      ports:
        - containerPort: 8081
---
apiVersion: v1
kind: Service
metadata:
  labels:
    run: pgweb
  name: pgweb-svc
spec:
  ports:
    - port: 8081
      targetPort: 8081
      protocol: TCP
  type: NodePort
  selector:
    run: pgweb
```
