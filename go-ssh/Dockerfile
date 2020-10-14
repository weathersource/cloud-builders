FROM golang:1.14-alpine

WORKDIR /go/src/app
COPY . .

RUN apk add --update --no-cache git build-base openssh

CMD ["app"]
