# Install Apache Airflow
reference: https://github.com/apache/airflow/tree/main/chart

### Run:
```commandline
helm repo add kedacore https://kedacore.github.io/charts
helm repo update
helm install keda kedacore/keda --namespace keda --create-namespace
```
### To uninstall keda you should remove resources you have created:
```commandline
kubectl delete $(kubectl get scaledobjects,scaledjobs -oname)
helm uninstall keda -n keda
```

### References:
- [Deploying KEDA](https://keda.sh/docs/2.8/deploy/#helm)