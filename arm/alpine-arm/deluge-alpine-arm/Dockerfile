FROM tokinring/alpine-arm
MAINTAINER TokinRing [support@gnetsolutions.net]

RUN printf 'http://mirror.clarkson.edu/alpine/edge/testing\n' >> /etc/apk/repositories && apk --no-cache add boost-python deluge py2-pip supervisor tor && pip install --no-cache-dir incremental constantly packaging automat service_identity && mkdir -p /root/.config/deluge

COPY ./config/supervisord.conf /etc/
COPY ./config/deluge-core.conf /root/.config/deluge/core.conf
COPY ./config/deluge-web.conf /root/.config/deluge/web.conf
COPY ./config/deluge-blocklist.conf /root/.config/deluge/blocklist.conf
COPY ./config/torrc /etc/tor/

RUN  chown -R root /var/lib/tor /etc/tor

EXPOSE 8112 54889

VOLUME ./torrents /torrents

CMD ["supervisord", "-c", "/etc/supervisord.conf"]
