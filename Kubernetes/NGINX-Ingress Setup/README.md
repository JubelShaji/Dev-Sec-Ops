## Install NGINX Ingress Controller
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.14.0/deploy/static/provider/cloud/deploy.yaml
```

## Edit Ingress Service
```
kubectl -n ingress-nginx edit svc ingress-nginx-controller
```
### Change under 'spec' :
```
spec:
  type: NodePort
  ports:
    - name: http
      port: 80
      targetPort: http
      nodePort: 30000       # Choose a port 30000-32767
    - name: https
      port: 443
      targetPort: https
      nodePort: 30443       # Choose a port 30000-32767
```

## Create 'ingress.yaml' and apply in kubernetes :
```
kubectl apply -f ingress.yaml
```
