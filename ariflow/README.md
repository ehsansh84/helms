# Install Apache Airflow
reference: https://github.com/apache/airflow/tree/main/chart

### Run:
```commandline
helm repo add apache-airflow https://airflow.apache.org
helm upgrade --install airflow apache-airflow/airflow --namespace airflow --create-namespace
```

### References:
- [Helm Chart for Apache Airflow](https://airflow.apache.org/docs/helm-chart/stable/index.html)