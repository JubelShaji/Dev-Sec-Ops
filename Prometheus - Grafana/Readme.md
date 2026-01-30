## Node Exporter to monitor host machine
```
docker run -d \
  --name node-exporter \
  --restart unless-stopped \
  --net="host" \
  --pid="host" \
  -v "/:/host:ro,rslave" \
  prom/node-exporter \
  --path.rootfs=/host

```

# Prometheus

## Create Directories :
```
mkdir -p monitoring/prometheus
```
```
Create 'docker-compose.yml' inside monitoring
Create 'prometheus.yml' inside prometheus
```
## Token and CA-Certificate
### Inside  prometheus directory create 'k8s-ca.crt'
#### Copy from Kubernetes Control-pane
```
cat /etc/kubernetes/pki/ca.crt
```
### Inside  prometheus directory create 'k8s-token'
#### From Kubernetes Control-pane
#### Create and apply 'prometheus-token.yaml'
```
kubectl apply -f prometheus-token.yaml
```
#### Create a file 'k8s-secret-token' with secret-token
```
kubectl -n monitoring get secret prometheus-ext-token   -o jsonpath='{.data.token}' | base64 -d > k8s-secret-token
```
#### Copy from 'k8s-secret-token' and to create 'k8s-token'
```
cat k8s-secret-token
```
### Create 'docker-compose.yml' and run :
```
nano docker-compose.yml
docker compose up -d
```
