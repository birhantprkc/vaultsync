FROM golang:1.26-alpine@sha256:70b46548e42db77e0966aaf3619fd068734dc6c77584d526b91126504fd95816 AS builder

WORKDIR /src
COPY main.go .
RUN CGO_ENABLED=0 go build -trimpath -buildvcs=false -ldflags="-s -w" -o /runtime-packaging-mock main.go

FROM scratch
COPY --from=builder /runtime-packaging-mock /runtime-packaging-mock
ENTRYPOINT ["/runtime-packaging-mock"]
