FROM golang as builder
WORKDIR /app
COPY go.mod .
COPY cmd ./cmd
RUN cd cmd/app && CGO_ENABLED=0 go build -o /app/app

FROM scratch
ADD ./html html
COPY --from=builder /app/app .
ENTRYPOINT [ "/app" ]
EXPOSE 8080