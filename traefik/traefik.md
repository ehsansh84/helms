# Run Traefik ingress controller

Original helm repository: https://github.com/traefik/traefik-helm-chart/tree/master/traefik

### Finally run:
```
kubectl create ns traefik
helm repo add traefik https://helm.traefik.io/traefik 
helm install -n traefik traefik traefik/traefik -f values.yaml
```
