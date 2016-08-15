FROM resin/rpi-raspbian:jessie
Maintainer martin dilger <martin@effectivetrainings.de>

RUN apt-get update && \
    apt-get install -y wget ca-certificates

ENV KAPACITOR_VERSION 1.0.0~beta4_armhf
RUN wget --no-check-certificate https://dl.influxdata.com/kapacitor/releases/kapacitor_${KAPACITOR_VERSION}.deb && \
    dpkg -i kapacitor_${KAPACITOR_VERSION}.deb && \
    rm -f kapacitor_${KAPACITOR_VERSION}.deb*
COPY kapacitor.conf /etc/kapacitor/kapacitor.conf

EXPOSE 9092

VOLUME /var/lib/kapacitor

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
CMD ["kapacitord"]
