# NOTE: building this requires it to have the build context of the repository root
FROM golang:1.12-alpine
LABEL maintainer="The Prometheus Authors <prometheus-developers@googlegroups.com>"

RUN apk add --update make git

ENV PROMBENCH_DIR /prombench
ENV PROMBENCH_REPO https://github.com/nikita-mk/test-prombench.git

COPY prombench /usr/bin/prombench
COPY cmd/prombench/clone.sh /usr/bin/clone.sh

ENTRYPOINT ["/usr/bin/clone.sh"]

WORKDIR $PROMBENCH_DIR
