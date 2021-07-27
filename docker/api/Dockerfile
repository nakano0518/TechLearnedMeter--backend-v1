# https://docs.docker.com/language/golang/build-images/  
# https://github.com/docker-library/golang/blob/54aa949c354b1e14cb636539f401b0e58ca76927/1.16/alpine3.14/Dockerfile

# ---------------------------------------------------
FROM golang:1.16-alpine as dev

WORKDIR /go/dev

# 1.16以降デフォルトでonだが
ENV GO111MODULE on

# Air(ホットリロード)導入⇒go get必要⇒内部でgitコマンド必要
RUN apk update \
  && apk add git \
  && go install github.com/cosmtrek/air@latest

COPY go.mod .
COPY go.sum .
RUN go mod download

COPY *.go .

# --------------------------------------------------
FROM golang:1.16-alpine as build

WORKDIR /go/build

COPY --from=dev /go/dev /go/build

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build /bin/main.go 


# --------------------------------------------------
FROM alpine:3.14.0 as prod

WORKDIR /go/src

RUN apk add --no-cache ca-certificates

COPY --from=build /go/build/bin/main /go/src/main

EXPOSE 5000

CMD ['/go/src/main']


