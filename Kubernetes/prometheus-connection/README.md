## To install node-exporter in worker nodes:
### Create 'node-exporter.yaml' and apply in kubernetes :
```
kubectl apply -f node-exporter.yaml
```

## Prometheus permission to access K8s-API:
``` 
Create 'prometheus-sa_rbac.yaml' and apply in kubernetes
```
```
kubectl create token prometheus --duration=24h
```
