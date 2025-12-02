# This base image is defined in build.json (HA chooses the arch)
#ARG BUILD_FROM
#FROM ${BUILD_FROM}
FROM homeassistant/home-assistant:stable

# Creates an image for a hass.io add-on that contains enough software to bother your Flashforge Finder and publish its info.
# This hass.io addon is based on 01F0's project here: https://github.com/01F0/flashforge-finder-api

#install environment
RUN apk add --no-cache --virtual build-deps alpine-sdk cmake git \
            python python-dev py-pip build-base
RUN pip install flask flask-cors --upgrade
RUN git clone https://github.com/johnpdowling/flashforge-finder-api.git /fff-api
    
# Copy services
COPY rootfs /
