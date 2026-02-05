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
#### Copy token
```
kubectl -n monitoring get secret prometheus-ext-token   -o jsonpath='{.data.token}' | base64 -d
```

## Run docker-compose file :
```
docker compose up -d
```
