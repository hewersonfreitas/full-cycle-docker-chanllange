FROM golang:1.22.0 AS builder

WORKDIR /app

COPY go.mod app.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o /app app.go

FROM scratch
COPY --from=builder /app /app
ENTRYPOINT [ "./app" ]