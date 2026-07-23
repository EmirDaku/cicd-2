FROM golang:1.25-alpine AS builder

WORKDIR /upper

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN CGO_ENABLED=0 go build -o main .

FROM scratch

COPY --from=builder /upper/main .

ENTRYPOINT ["./main"]