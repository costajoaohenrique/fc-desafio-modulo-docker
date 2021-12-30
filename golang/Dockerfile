FROM golang:alpine as stage-build

WORKDIR /usr/src/app

COPY . .

RUN go mod init example/hello

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" .
    
FROM scratch

WORKDIR /app

COPY --from=stage-build /usr/src/app/hello /usr/bin/

ENTRYPOINT ["hello"]



