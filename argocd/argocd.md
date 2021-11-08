# Run ArgoCD

Original helm repository: https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd

### Run:
```
kubectl create namespace argocd
helm repo add argo https://argoproj.github.io/argo-helm
helm install -n argocd argocd argo/argo-cd
```
