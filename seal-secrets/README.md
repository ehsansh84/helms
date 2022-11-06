# Install bitnami seal secrets

Original helm repository: https://github.com/bitnami-labs/sealed-secrets

### run:
```
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets 
helm install sealed-secrets -n kube-system --set-string fullnameOverride=sealed-secrets-controller sealed-secrets/sealed-secrets -f values.yaml
```
