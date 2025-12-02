ARG BUILD_FROM
FROM ${BUILD_FROM}

#install environment
RUN apk add --no-cache --virtual build-deps alpine-sdk cmake git \
            python python-dev py-pip build-base
RUN pip install flask flask-cors --upgrade
RUN git clone https://github.com/paulsbroomfield/flashforge-finder-api.git /fff_api
    
# Copy services
COPY rootfs /
