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
   password: "^Avnsdhj6534"
   coreDatabase: "registry"
   notaryServerDatabase: "notary_server"
   notarySignerDatabase: "notary_signer"
```

### Finally run:
```
$ helm repo add harbor https://helm.goharbor.io
$ helm install harbor harbor/harbor --values=harbor.yaml
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
