FROM golang:alpine3.22 as builder
ARG CGO_ENABLED=0
ARG GOOS=linux
WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=$CGO_ENABLED GOOS=$GOOS go build -o main ./cmd/api

FROM alpine:3.22
WORKDIR /app
COPY --from=builder /app/main .

EXPOSE 8081

CMD ["./main"]