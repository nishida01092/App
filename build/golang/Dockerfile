FROM golang:1.19.6-alpine as builder

WORKDIR /build

COPY ../../go.mod ../../go.sum ./

RUN go mod download

COPY ../../ ./

USER app

RUN go build \
    -o /go/bin/main \
    -ldflags '-s -w'

FROM alpine as runner

COPY --from=builder /build/golang /opt/app/

CMD ["/opt/app/golang"]