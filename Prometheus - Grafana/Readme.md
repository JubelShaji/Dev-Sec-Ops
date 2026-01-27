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
### Create directory :
```
mkdir -p monitoring/prometheus
```
### Create Configuration File :
```
prometheus.yml
```
### Create 'docker-compose.yml' and run :
```
docker compose up -d
```
