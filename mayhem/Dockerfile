# Build Stage:
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ="America/New York"
RUN apt-get update && apt-get install -y build-essential libexif-dev fontconfig libx11-dev libxft-dev libimlib2-dev libgif-dev

## Add Source Code
ADD *.c /
ADD *.h /
ADD *.lst /
ADD *.1 /
ADD icon /icon
ADD exec /exec
ADD Makefile /

## Build Step
RUN make clean all

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04
COPY --from=builder /sxiv /
RUN apt-get update && apt install -y libexif12 fontconfig libx11-6 libxft2 libimlib2 libgif7
