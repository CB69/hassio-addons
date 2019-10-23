ARG BUILD_FROM
FROM $BUILD_FROM

# Add env
ENV LANG C.UTF-8

#Install things
ARG VERSION_PJSIP=2.9

RUN apk add --no-cache python2 py2-paho-mqtt bash curl wget tar \
    && curl -L https://raw.githubusercontent.com/CB69/CBsip2mqtt/master/CBsip2mqtt.py -o CBsip2mqtt.py \
    && apk add --no-cache --virtual .build4pjsip alpine-sdk \
    && apk add --no-cache libsrtp-dev python2-dev openssl-dev opus-dev \
    && cd \
    && wget -qnv "http://www.pjsip.org/release/$VERSION_PJSIP/pjproject-$VERSION_PJSIP.tar.bz2" -O - | tar xjf - \
    && cd pjproject-$VERSION_PJSIP \
    && ./configure --with-external-srtp --enable-shared --disable-sound --disable-oss --disable-sdl --disable-speex-aec --disable-video --prefix=/usr/local > /dev/null \
    && make dep \
    && make \
    && make install \
    && cd pjsip-apps/src/python \
    && make \
    && make install \
    && cd \
    && rm -rf pjproject-$VERSION_PJSIP \
    && apk del .build4pjsip

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]

