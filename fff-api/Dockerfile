ARG BUILD_FROM
FROM $BUILD_FROM

# Install packages
RUN apk add --no-cache python3 py3-pip git

# Upgrade pip & install Python deps
RUN pip3 install --no-cache-dir --upgrade pip && \
    pip3 install --no-cache-dir flask flask-cors pyserial

# Copy API
RUN git clone https://github.com/johnpdowling/flashforge-finder-api.git /opt/fff-api
WORKDIR /opt/fff-api

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
