FROM golang:1.21 as build
WORKDIR /app/
COPY go.mod go.sum ./
RUN go mod download
COPY ./integration-tests/configs/otel-metrics-gen/ ./
RUN CGO_ENABLED=0 go build -o main main.go
FROM alpine:3.18
COPY --from=build /app/main /app/main
CMD ["/app/main"]
