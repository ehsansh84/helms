# How to install Grafana/Loki on kubernetes?  

```commandline
kubectl create namespace loki
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install loki grafana/loki-stack -n loki  -f values.yaml
```
