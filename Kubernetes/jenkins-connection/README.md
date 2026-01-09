### 1 ) Create jenkins-sa_rbac.yaml and apply in Kubernetes
```
kubectl apply -f jenkins-sa_rbac.yaml
```

### 2 ) Create regcred secret for kaniko :
```
kubectl create secret docker-registry regcred \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=<your-dockerhub-username> \
  --docker-password=<your-dockerhub-password> \
  --docker-email=<your-email>
```

## Kubernetes Cofiguration in jenkins :
### Manage jenkins -> Cloud -> New Cloud -> Kubernetes
```
Kubernetes url   : https://<API-SERVER-IP>:6443 ( kubectl cluster-info )
server certificate   : Copy ca.art  ( cat /etc/kubernetes/pki/ca.crt )
Kubernetes Namespace : default
Credentials      : create secret text ( kubectl create token jenkins --duration=24h )
```
