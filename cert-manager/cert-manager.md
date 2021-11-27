# Run Cert manager

Original helm repository: https://github.com/bitnami/charts/tree/master/bitnami/cert-manager/

### Finally run:
```
kubectl create namespace cert-man
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install cert-man bitnami/cert-manager -n cert-man
```
