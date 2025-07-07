# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}" \
# Download latest teslamate-abrp script and requirements at build time
 && mkdir -p /usr/share/teslamate-abrp \
 && curl -sSLf -o /usr/share/teslamate-abrp/teslamate_mqtt2abrp.py "https://raw.githubusercontent.com/fetzu/teslamate-abrp/main/teslamate_mqtt2abrp.py" \
 && curl -sSLf -o /usr/share/teslamate-abrp/requirements.txt "https://raw.githubusercontent.com/fetzu/teslamate-abrp/main/requirements.txt"

# Copy root filesystem
COPY rootfs /
