ARG ARCH="amd64"
ARG OS="linux"

FROM golang:1.12-alpine AS builder
ENV GO111MODULE=on
RUN apk add --update --no-cache git
COPY . /src
WORKDIR /src
RUN go build -a -tags netgo -o /src/build/amGithubNotifier

FROM quay.io/prometheus/busybox-$OS-$ARCH:latest
LABEL maintainer="The Prometheus Authors <prometheus-developers@googlegroups.com>"
COPY --from=builder /src/build/amGithubNotifier /bin/amGithubNotifier
ENTRYPOINT ["/bin/amGithubNotifier"]
