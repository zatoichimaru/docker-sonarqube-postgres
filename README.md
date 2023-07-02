# Install Sonarqube 10 e Postgres 15 

### Windows configuration

# Open Powershell
```
wsl -d docker-desktop sysctl -w vm.max_map_count=262144
```
ou
```
wsl -d docker-desktop echo "vm.max_map_count = 262144" > /etc/sysctl.d/99-docker-desktop.conf
```
### Linux configuration

# Open Terminal
```
sudo sysctl -w vm.max_map_count=262144
```
ou
```
sudo echo "vm.max_map_count = 262144" > /etc/sysctl.d/99-docker-desktop.conf
```

### POSTGRES Environments:
```
    POSTGRES_VERSION=15

    POSTGRES_PROD_USER=sonar_prod
    POSTGRES_PROD_PASSWORD=sonar_prod
    POSTGRES_PROD_DB=sonar_prod
    POSTGRES_PROD_PORT=5432

    POSTGRES_QA_USER=sonar_qa
    POSTGRES_QA_PASSWORD=sonar_qa
    POSTGRES_QA_DB=sonar_qa
    POSTGRES_QA_PORT=5433
```

### SONAR Environments:
```
    SONAR_VERSION=10.1.0-community

    SONARQUBE_PROD_JDBC_URL=jdbc:postgresql://postgres_prod:5432/sonar_prod
    SONARQUBE_PROD_JDBC_USERNAME=sonar_prod
    SONARQUBE_PROD_JDBC_PASSWORD=sonar_prod
    SONARQUBE_PROD_PORT=9000

    SONARQUBE_QA_JDBC_URL=jdbc:postgresql://postgres_qa:5432/sonar_qa
    SONARQUBE_QA_JDBC_USERNAME=sonar_qa
    SONARQUBE_QA_JDBC_PASSWORD=sonar_qa
    SONARQUBE_QA_PORT=9000
```
### Execution

# Step 1
```
  cd postgres
  docker compose up --env-file=.env up --build -d

```
# Step 2
```
  cd sonarqube
  docker compose up --env-file=.env up --build -d

```