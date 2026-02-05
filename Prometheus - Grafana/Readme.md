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
## Inside  prometheus directory create 'k8s-token'
### Copy from Kubernetes Control-pane
#### From Kubernetes Control-pane :
#### Create and apply 'prometheus-token.yaml'
```
kubectl apply -f prometheus-token.yaml
```
#### Create a file 'k8s-token'
```
kubectl -n monitoring get secret prometheus-ext-token   -o jsonpath='{.data.token}' | base64 -d > k8s-token
```
#### Copy contents of 'k8s-token' from k8s Control Pane
```
cat k8s-token
```
### Create 'docker-compose.yml' and run :
```
nano docker-compose.yml
docker compose up -d
```
