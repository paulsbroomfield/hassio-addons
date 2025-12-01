ARG BUILD_FROM
FROM ${BUILD_FROM}

# ==============================
# Install packages
# ==============================
RUN apk add --no-cache \
    python3 \
    py3-pip \
    python3-dev \
    git \
    build-base

# Upgrade pip & install Python deps
RUN pip3 install --no-cache-dir --upgrade pip && \
    pip3 install --no-cache-dir flask flask-cors pyserial

# ==============================
# Copy Flashforge API
# ==============================
RUN git clone https://github.com/johnpdowling/flashforge-finder-api.git /opt/fff-api
WORKDIR /opt/fff-api

# ==============================
# Copy rootfs
# ==============================
COPY rootfs /

# ==============================
# Build arguments
# ==============================
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# ==============================
# Metadata
# ==============================
LABEL \
    io.hass.name="Flashforge 3D Printer API Server" \
    io.hass.description="A Flask API server that communicates with your Flashforge Finder." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    org.label-schema.build-date="${BUILD_DATE}" \
    org.label-schema.name="Flashforge-3D-Printer-API Server" \
    org.label-schema.schema-version="1.0"
