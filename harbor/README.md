# Run Harbor on an existing postgresql

Original helm repository: https://github.com/goharbor/harbor-helm
### Making database external:
```yaml
database:
  type: external
```
### Setting external database configurations:
```yaml
external:
   host: "postgres-postgresql"
   port: "5432"
   username: "postgres"
   password: "ilQ7lUqd2B"
   coreDatabase: "registry"
   notaryServerDatabase: "notary_server"
   notarySignerDatabase: "notary_signer"
```

### Finally run:
```
kubectl create namespace harbor
helm repo add harbor https://helm.goharbor.io
helm install -n harbor harbor harbor/harbor --values=values.yaml
```

To run harbor you must create 3 databases:
- registry
- notary_server
- notary_signer
The command for creating in Postgres is:
```
CREATE DATABASE registry;
CREATE DATABASE notary_server;
CREATE DATABASE notary_signer;
```

