# Install kong
reference: https://github.com/Kong/charts

### Run:
```commandline
helm repo add kong https://charts.konghq.com
helm repo update
helm install kong/kong --name=kong --set ingressController.installCRDs=false -n kong --create-namespace
```
