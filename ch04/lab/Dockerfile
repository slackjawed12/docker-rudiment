FROM diamol/golang AS builder

COPY main.go .
RUN go build -o /server

FROM diamol/base
ENV USER=sixeyed
CMD ["/web/server"]

WORKDIR /web
EXPOSE 80

COPY --from=builder /server .
RUN chmod +x /web/server
COPY index.html .