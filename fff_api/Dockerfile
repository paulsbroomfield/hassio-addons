ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.20
FROM $BUILD_FROM

# Install packages
RUN apk add --no-cache python3 py3-pip git

# Upgrade pip & install Python deps
RUN apk add --no-cache --virtual build-deps alpine-sdk cmake git \
            python python-dev py-pip build-base
RUN pip install flask flask-cors --upgrade

# Copy API
RUN git clone https://github.com/paulsbroomfield/flashforge-finder-api.git /opt/fff_api
WORKDIR /opt/fff_api

# Copy rootfs
COPY rootfs /

# Labeling
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION
LABEL \
  io.hass.name="Flashforge 3D Printer API Server" \
  io.hass.description="API server talking to Flashforge Finder" \
  io.hass.arch="${BUILD_ARCH}" \
  io.hass.type="addon" \
  io.hass.version="${BUILD_VERSION}"
