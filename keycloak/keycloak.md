# Run Keycloak using 3 replicas on specific nodes

Original helm repository: https://github.com/bitnami/charts/tree/master/bitnami/keycloak

This installation uses an external Postgres instance, So you should provide information like this:
```yaml
postgresql:
  enabled: false
externalDatabase:
  host: "postgres-postgresql.postgres"
  port: 5432
  user: postgres
  password: "sCneXId5Wh"
  database: keycloak
```
and create a database named `keycloak` inside the instance using this command:
```
CREATE DATABASE keycloak;
```

### Finally run:
```
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install keycloak bitnami/keycloak
```

