FROM python:3.9-slim as builder

# Upgrade pip to the latest.
RUN pip install --upgrade pip
RUN pip install --no-cache-dir python-swiftclient


FROM python:3.9-slim

COPY --from=builder /usr/local/ /usr/local/

WORKDIR /usr/src/app
