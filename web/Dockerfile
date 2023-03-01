## Build
FROM golang:1.19-buster AS build

WORKDIR /app
ENV PORT=8001

COPY go.mod ./
RUN go mod download

COPY *.go ./

RUN go build -o /web

## Deploy
FROM gcr.io/distroless/base

WORKDIR /

COPY --from=build /web /web

EXPOSE 8001

USER nonroot:nonroot

ENTRYPOINT ["/web"]