FROM python:3.11-slim as builder

RUN apt-get update \
    && apt-get install -y autoconf gcc libc-dev liberasurecode-dev libffi-dev libmagic-dev libnsl-dev libssl-dev libtool make zlib1g-dev

# Upgrade pip to the latest.
RUN pip install --upgrade pip
RUN pip install --no-cache-dir swift


FROM python:3.11-slim as libs

RUN apt-get update \
    && apt-get install -y liberasurecode1


FROM python:3.11-slim

COPY --from=libs /usr/ /usr/
COPY --from=libs /etc/ /etc/
COPY --from=builder /usr/local/ /usr/local/

RUN echo "/usr/local/lib" > /etc/ld.so.conf.d/local.conf \
    ; ldconfig

WORKDIR /usr/src/app
