FROM alpine:3.7 as builder

LABEL maintainer="muchrm.me@gmail.com"

ENV DESTDIR /opt/unit/
ENV UNIT_VERSION 1.0
RUN apk add --update --no-cache build-base curl 

RUN curl -O https://unit.nginx.org/download/unit-$UNIT_VERSION.tar.gz
RUN tar -xvf /unit-$UNIT_VERSION.tar.gz \
    && mv /unit-$UNIT_VERSION /unit

WORKDIR /unit
RUN ./configure && make && make install

FROM alpine:3.7
COPY --from=builder /opt/unit /opt/unit
COPY --from=builder /unit /unit
CMD ["/opt/unit/sbin/unitd", "--no-daemon", "--control", "unix:/var/run/control.unit.sock"]