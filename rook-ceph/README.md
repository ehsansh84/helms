# Install Rook ceph

Original helm repository: https://rook.io/docs/rook/v1.8/helm-operator.html

### run:
```
kubectl create ns rook-ceph
helm repo add rook-release https://charts.rook.io/release 
helm install -n rook-ceph rook-ceph rook-release/rook-ceph
```
