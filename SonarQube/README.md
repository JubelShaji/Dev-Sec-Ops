## Create a Docker network
```
docker network create sonarnet
```

## Run PostgreSQL container
```
docker run -d --name sonardb \
  --network sonarnet \
  -e POSTGRES_USER=sonar \
  -e POSTGRES_PASSWORD=sonar_password \
  -e POSTGRES_DB=sonarqube \
  -v sonardb_data:/var/lib/postgresql/data \
  postgres:15
```

## Run SonarQube container
```
docker run -d --name sonarqube \
  --network sonarnet \
  -p 9000:9000 \
  -e SONAR_JDBC_URL=jdbc:postgresql://sonardb:5432/sonarqube \
  -e SONAR_JDBC_USERNAME=sonar \
  -e SONAR_JDBC_PASSWORD=sonar_password \
  -v sonarqube_data:/opt/sonarqube/data \
  sonarqube:community
```
