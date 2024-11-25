FROM golang:1.23.3-bookworm AS builder
WORKDIR /app
COPY app.go .
RUN go mod init main && \
	CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -o main --ldflags="-extldflags=-static"

FROM scratch
EXPOSE 80
COPY --from=builder /app/main /main
CMD ["/main"]
