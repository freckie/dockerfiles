# idea from github.com/Budry/cadvisor-arm

# Builder
FROM arm32v7/golang as builder

ENV CADVISOR_VERSION "release-v0.32"

RUN apt update && apt install -y git dmsetup && apt clean
RUN git clone --branch ${CADVISOR_VERSION} https://github.com/google/cadvisor.git /go/src/github.com/google/cadvisor

WORKDIR /go/src/github.com/google/cadvisor

RUN make build

# Image for usage
FROM arm32v7/debian

COPY --from=builder /go/src/github.com/google/cadvisor/cadvisor /usr/bin/cadvisor

EXPOSE 8080

ENTRYPOINT ["/usr/bin/cadvisor", "-logtostderr"]