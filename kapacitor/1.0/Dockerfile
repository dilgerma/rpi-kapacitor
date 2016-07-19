FROM resin/rpi-raspbian:jessie
Maintainer martin dilger <martin@effectivetrainings.de>

RUN apt-get update && \
    apt-get install wget

ENV KAPACITOR_VERSION 1.0.0~beta3_armhf
RUN wget --no-check-certificate https://dl.influxdata.com/kapacitor/releases/kapacitor_${KAPACITOR_VERSION}.deb && \
    dpkg -i kapacitor_${KAPACITOR_VERSION}.deb && \
    rm -f kapacitor_${KAPACITOR_VERSION}.deb*

EXPOSE 9092

VOLUME /var/lib/kapacitor

COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
CMD ["kapacitord"]
