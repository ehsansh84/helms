# Run ArgoCD

Original helm repository: https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd

### Run:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
