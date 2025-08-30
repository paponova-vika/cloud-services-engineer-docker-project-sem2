FROM golang:alpine3.22 as builder
ARG CGO_ENABLED
ARG GOOS

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN CGO_ENABLED=$CGO_ENABLED GOOS=$GOOS go build -o main ./cmd/api

FROM alpine:3.22.1

RUN addgroup -g 1000 gouser && \
    adduser -D -u 1000 -G gouser gouser
RUN apk add --no-cache  curl
    
WORKDIR /app
COPY --from=builder /app/main .
USER gouser:gouser

EXPOSE 8081

CMD ["./main"]