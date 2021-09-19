#ARG BUILD_FROM="alpine:latest"
ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

# Install requirements for add-on
RUN apk add --no-cache jq npm make gcc g++ python3 linux-headers udev
RUN npm init -f
RUN npm install mqtt -g
RUN apk add --no-cache nodejs
RUN apk add --no-cache make gcc g++ python3 linux-headers udev
RUN npm install serialport --build-from-source

WORKDIR /share

RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
