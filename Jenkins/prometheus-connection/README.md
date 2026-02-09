## For Monitoring :
### Node Exporter (for host monitoring) :
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

### Install Plugin (To monitor jenkins app)
```
Install 'Prometheus metrics plugin' and restart
```
