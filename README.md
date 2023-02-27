# Platform Engineer Challenge

The files in the original repository have been moved to match the following folder structure:
* deployments - contains all the YAML configuration files
* pgsql - Docker files for PostgreSQL and database seed
* src - Go server source files and Docker configuration

## Running the service in Docker

### Postgres Database

The database is a dependency for the main service and must be run first.
```
cd pgsql
docker build -f Dockerfile.dev -t pgsql .
docker run -d -p 5432:5432  -e POSTGRES_PASSWORD=password --name pgsql-container pgsql
```

### Go HTTP Server

```
cd src
docker build -f Dockerfile.dev -t go-http .
docker run -d -p 8080:8080 --name go-gttp-container go-http
```

## Running the service in Kubernetes

### Using kubectl

Steps to deploy both the service and the database in a Kubernetes cluster:
```
cd deployments
kubectl apply -f deployment.yaml
```

### Using Helm

In the deployments folder there is also a template Helm configurations for the Go service:
```
helm install go-http .\go-http
```
or
```
helm upgrade go-http .\go-http
```