# This base image is defined in build.json (HA chooses the arch)
ARG BUILD_FROM
FROM ${BUILD_FROM}

# Set up addon environment
ENV LANG C.UTF-8

# Copy root filesystem (if you create /rootfs structure)
# COPY rootfs/ /

# Copy your application into the container
WORKDIR /app
COPY . /app

# Install Python dependencies
# If you have requirements.txt — otherwise remove this line
RUN pip install --no-cache-dir -r requirements.txt || true

# Home Assistant requires this entrypoint to stay in foreground
CMD [ "python3", "/api/app.py" ]
