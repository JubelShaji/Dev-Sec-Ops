## To start Jenkins :
```
docker run -d \
  --name jenkins \
  --restart unless-stopped \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

## Jenkins-agent with trivy installed :
```
The Dockerfile here builds jenkins-agent image  with trivy installed , build and push this image to a registry which kubernetes can access. It is referenced in  jenkinsfile.
```

## Get Jenkins Initial Admin Password :
```
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

## Create regcred secret for kaniko :
```
kubectl create secret docker-registry regcred \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=<your-dockerhub-username> \
  --docker-password=<your-dockerhub-password> \
  --docker-email=<your-email>
```

##  Configure Kubernets cloud in jenkins:
### Manage Jenkins -> Cloud -> New Cloud -> Kubernets ->
```
Name : Kubernets
Kubernetes Namespace : jenkins
Jenkins URL : http://jenkins.jenkins.svc.cluster.local:8080
Jenkins tunnel : jenkins.jenkins.svc.cluster.local:50000
```

## Jenkins pipeline job name :
```
Use ' voteapp ' , otherwise change path of kaniko build context for every build in the pipeline.
```
