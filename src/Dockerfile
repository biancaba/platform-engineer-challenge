FROM golang:alpine
RUN mkdir /app
COPY . /app
WORKDIR /app
RUN go build -o simple-http-server . 
CMD ["/app/simple-http-server", "--db", "postgresql://postgres:root@10.103.10.96/postgres?sslmode=disable"]