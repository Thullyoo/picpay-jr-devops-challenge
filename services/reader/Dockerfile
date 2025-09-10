FROM golang:1.22 AS builder

WORKDIR /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go

COPY go.mod /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go
COPY go.sum /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go

RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .


FROM builder AS tester
RUN go test -v ./...

FROM alpine AS release

WORKDIR /app

COPY --from=builder /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go/main .

EXPOSE 8080

CMD ["./main"]
