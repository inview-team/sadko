FROM golang:latest AS builder
ENV PROJECT_PATH=/app/lct
ENV CGO_ENABLED=0
ENV GOOS=macos
COPY . ${PROJECT_PATH}
WORKDIR ${PROJECT_PATH}
RUN go build cmd/main.go

FROM golang:alpine
WORKDIR /app/cmd
COPY --from=builder /app/cmd/main .
EXPOSE 30002
CMD ["./main"]