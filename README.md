# Platform Engineer Challenge

## Running the service in Docker

### Postgres Database

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
