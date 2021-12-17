# Run Cert manager

Original helm repository: https://github.com/bitnami/charts/tree/master/bitnami/cert-manager/

### Finally run:
```
kubectl create namespace cert-man
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install cert-man bitnami/cert-manager -n cert-man
```

You may need to create CRDs after installation:
```commandline
kubectl apply -f https://github.com/jetstack/cert-manager/releases/download/v1.6.1/cert-manager.crds.yaml
```
