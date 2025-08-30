FROM golang:alpine3.22 as builder
ARG CGO_ENABLED=0
ARG GOOS=linux

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN CGO_ENABLED=$CGO_ENABLED GOOS=$GOOS go build -o main ./cmd/api

FROM alpine:3.22.1

RUN groupadd -g 1000 gouser && \
    useradd -r -u 1000 -g gouser gouser \
RUN apk add --no-cache  curl \
    
WORKDIR /app
COPY --from=builder /app/main .
USER gouser

EXPOSE 8081

CMD ["./main"]