### 1 ) Create jenkins-sa_rbac.yaml and apply in Kubernetes
```
kubectl apply -f jenkins-sa_rbac.yaml
```

### 2 ) Token and Server Certificate Key
```
kubectl create token jenkins

cat /etc/kubernetes/pki/ca.crt
```

## Kubernetes Cofiguration in jenkins :
### Manage jenkins -> Cloud -> New Cloud -> Kubernetes
```
Kubernetes url   : https://<API-SERVER-IP>:6443 ( kubectl cluster-info )
server certificate   : Copy ca.art  ( cat /etc/kubernetes/pki/ca.crt )
Kubernetes Namespace : default
Credentials      : create secret text ( kubectl create token jenkins )
```