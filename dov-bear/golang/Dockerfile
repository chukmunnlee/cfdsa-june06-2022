FROM golang:alpine3.16 AS builder

WORKDIR /app

ADD go.mod .
ADD go.sum .
ADD main.go .

# produces the main (executable)
RUN go build -o main main.go

FROM alpine:3.16

LABEL org.opencontainers.image.source=https://github.com/chukmunnlee/cfdsa-june06-2022

WORKDIR /app

COPY --from=builder /app/main main
ADD public public
ADD templates templates

ENV PORT=3000
EXPOSE ${PORT}

ENTRYPOINT [ "./main" ]