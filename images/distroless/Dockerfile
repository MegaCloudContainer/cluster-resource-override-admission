# Build the manager binary
FROM golang:1.20 as builder

ENV CGO_ENABLED 0
ENV GOOS linux
ENV GO_REQUIRED_MIN_VERSION ""

WORKDIR /workspace
COPY . .

RUN make build

FROM gcr.io/distroless/base:nonroot
WORKDIR /
COPY --from=builder /workspace/bin/cluster-resource-override-admission /usr/bin/cluster-resource-override-admission
USER 65532:65532
