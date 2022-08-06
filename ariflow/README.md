# Install Apache Airflow
reference: https://github.com/apache/airflow/tree/main/chart

### Run:
```commandline
helm repo add apache-airflow https://airflow.apache.org
helm upgrade --install airflow apache-airflow/airflow --namespace airflow --create-namespace
```
The default admin login credential is:
```
username: admin
password: admin
```
If not worked, go to `webserver` pod shell adn execute:
```commandline
airflow users  create --role Admin --username admin --email admin --firstname admin --lastname admin --password admin
```
### References:
- [Helm Chart for Apache Airflow](https://airflow.apache.org/docs/helm-chart/stable/index.html)