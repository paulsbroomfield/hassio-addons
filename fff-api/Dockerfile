ARG BUILD_FROM=ghcr.io/hassio-addons/base-aarch64:14.1.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Creates an image for a hass.io add-on that contains enough software to bother your Flashforge Finder and publish its info.
# This hass.io addon is based on 01F0's project here: https://github.com/01F0/flashforge-finder-api

#install environment
RUN apk add --no-cache \
    python3 \
    py3-pip \
    python3-dev \
    alpine-sdk \
    cmake \
    git \
    build-base

RUN pip3 install --upgrade pip
RUN pip3 install flask flask-cors

RUN git clone https://github.com/johnpdowling/flashforge-finder-api.git /fff-api
    
# Copy services
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Flashforge-3D-Printer-API Server" \
    io.hass.description="A Flask API server that will act as a conduit to your Flashforge Finder" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    #maintainer="John Dowling <john.patrick.dowling@gmail.com>" \
    org.label-schema.description="The Flashforge 3D Printer API Server program" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Flashforge-3D-Printer-API Server" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="" \
    #org.label-schema.usage="https://github.com/johnpdowling/hassio-addons/tree/master/fff-api/README.md" \
    #org.label-schema.vcs-ref=${BUILD_REF} \
    #org.label-schema.vcs-url="https://github.com/johnpdowling/hassio-addons/fff-api" \
    #org.label-schema.vendor="JPD Hass.io Add-ons"
