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

## Prometheus Configuration

### Create Configuration File :
```
mkdir -p monitoring/prometheus
cd monitoring
nano prometheus/prometheus.yml
```
### Token and CA-Certificate
```
Inside  prometheus directory create ...
k8s-ca.crt (/etc/kubernetes/pki/ca.crt)
k8s-token (kubectl -n monitoring create token prometheus --duration=24h)
```
### Create 'docker-compose.yml' and run :
```
nano docker-compose.yml
docker compose up -d
```
