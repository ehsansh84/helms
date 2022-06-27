# Install krakend
reference: https://medium.com/javarevisited/krakend-how-to-deploy-to-kubernetes-bd1bf2173b0

### `config.yaml`:
```yaml
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: krakend-cm
  labels:
    name: krakend-cm
data:
  krakend.json: |
    {
      "version": 2,
      "endpoints": []
      "extra_config": {}
    }
```
### `deployment.yml`
```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: krakend-deployment
  labels:
    name: krakend-deployment
    app: krakend
    tier: app
spec:
  replicas: 1
  selector:
    matchLabels:
      name: krakend-pod
      app: krakend
      tier: app
  template:
    metadata:
      name: krakend-pod
      labels:
        name: krakend-pod
        app: krakend
        tier: app
    spec:
      containers:
      - name: krakend-container
        image: devopsfaith/krakend:1.4.1-alpine
        command: ["/usr/bin/krakend"]
        args: ["run", "-d", "-c", "/etc/config/krakend/krakend.json", "-p", "8080"]
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 8080
        env:
        - name: KRAKEND_PORT
          value: "8080"
        volumeMounts:
        - name: config-volume
          mountPath: /etc/config/krakend
      volumes:
      - name: config-volume
        configMap:
          name: krakend-cm
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
```
### `service.yml`
```yaml
---
apiVersion: v1
kind: Service
metadata:
  name: krakend-svc
  labels:
    name: krakend-svc
spec:
  type: ClusterIP
  selector:
    name: krakend-pod
    app: krakend
    tier: app
  ports:
  - protocol: TCP
    targetPort: 8080
    port: 80
```
