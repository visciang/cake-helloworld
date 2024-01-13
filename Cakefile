ARG ALPINE_VERSION=3.19.0

compile:
    FROM alpine:${ALPINE_VERSION}
    RUN apk add --no-cache gcc libc-dev
    COPY hello.c .
    RUN gcc hello.c -o /hello

app:
    FROM alpine:${ALPINE_VERSION}
    COPY --from=+compile /hello /usr/bin/hello
    ENTRYPOINT ["/usr/bin/hello"]
