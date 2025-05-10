FROM golang:1.23 AS builder

WORKDIR /app
COPY . .
RUN go build -o app

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o app

FROM gcr.io/distroless/static:nonroot
WORKDIR /app
COPY --from=builder /app/app .
USER nonroot
EXPOSE 8080
CMD ["/app/app"]
