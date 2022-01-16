# Install sentry

Original helm repository: https://github.com/helm/charts/tree/master/stable/sentry

### run:
```
kubectl create ns sentry
helm repo add sentry https://sentry-kubernetes.github.io/charts 
helm install sentry sentry/sentry -n sentry -f values.yaml
```
