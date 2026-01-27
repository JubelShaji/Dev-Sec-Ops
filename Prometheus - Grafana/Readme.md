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
cd monitoring/prometheus
nano prometheus.yml
```
### Create 'docker-compose.yml' and run :
```
docker compose up -d
```
