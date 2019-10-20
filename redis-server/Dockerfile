FROM ubuntu:latest as builder

WORKDIR /usr/src/redis-stable/

RUN apt -y update
RUN apt install -y curl make gcc
RUN curl -SL http://download.redis.io/releases/redis-stable.tar.gz | tar -xzC /usr/src/
RUN make

FROM scratch

COPY --from=builder /usr/src/redis-stable/src/redis-server /
COPY --from=builder /usr/src/redis-stable/redis.conf /

COPY --from=builder /lib64/ld-linux-x86-64.so.2 /lib64/
COPY --from=builder /lib/x86_64-linux-gnu/libm.so.6 \
                    /lib/x86_64-linux-gnu/libdl.so.2 \
                    /lib/x86_64-linux-gnu/librt.so.1 \
                    /lib/x86_64-linux-gnu/libpthread.so.0 \
                    /lib/x86_64-linux-gnu/libc.so.6 \
                    /lib/x86_64-linux-gnu/

EXPOSE 6379/tcp
ENTRYPOINT ["/redis-server", "redis.conf"]