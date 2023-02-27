FROM golang:alpine
RUN mkdir /app
COPY . /app
WORKDIR /app
RUN go build -o simple-http-server . 
CMD ["/app/simple-http-server", "--db", "postgresql://postgres:password@127.0.0.1/postgres?sslmode=disable"]