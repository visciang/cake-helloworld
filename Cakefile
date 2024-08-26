ARG ALPINE_VERSION=3.19.0

devshell:
    @devshell
    FROM +toolchain

toolchain:
    FROM alpine:${ALPINE_VERSION}
    RUN apk add --no-cache gcc libc-dev

compile:
    FROM +toolchain
    COPY hello.c .
    RUN gcc -Wall -Werror hello.c -o /hello

app:
    FROM alpine:${ALPINE_VERSION}
    COPY --from=+compile /hello /usr/bin/hello
    ENTRYPOINT ["/usr/bin/hello"]
