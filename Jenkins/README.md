## To start Jenkins :
```
docker run -d \
  --name jenkins \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 50000:50000 \
  -e JAVA_OPTS="-Dorg.jenkinsci.plugins.durabletask.BourneShellScript.LAUNCH_DIAGNOSTICS=true" \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

## Get Jenkins Initial Admin Password :
```
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Jenkins pipeline job name :
```
Use ' voteapp ' , otherwise change path of kaniko build context for every build in the pipeline.
```

## Node Exporter :
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
