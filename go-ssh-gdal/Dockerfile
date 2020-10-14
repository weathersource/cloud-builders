# Uses official Dockerhub Golang image: https://hub.docker.com/_/golang
FROM golang:1.14

WORKDIR /go/src/app
COPY . .

RUN apt-get update -qqy && apt-get install -qqy openssh-server gdal-bin libgdal-dev

CMD ["app"]
