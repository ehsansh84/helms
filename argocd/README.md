# Run ArgoCD

Original helm repository: https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd

### Run:
```
kubectl create namespace argocd
helm repo add argo https://argoproj.github.io/argo-helm
helm install -n argocd argocd argo/argo-cd -f values.yaml
```

### If you want to use your own certificate produce `secret` like this:
```
kubectl create secret tls my-secret-name -n argocd --cert=path/to/cert/file --key=path/to/key/file
```

### get admin password:
```commandline
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```