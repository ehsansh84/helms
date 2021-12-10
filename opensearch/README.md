# Run Openshift


### run:
```
kubectl create namespace opensearch
helm repo add opensearch https://opensearch-project.github.io/helm-charts/
helm install opensearch -n opensearch opensearch/opensearch
```
