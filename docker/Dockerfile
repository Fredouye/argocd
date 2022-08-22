FROM alpine:3.15

LABEL org.opencontainers.image.authors="Frederic Mangeant <frederic.mangeant@gmail.com>"
LABEL org.opencontainers.image.version="5.5"
LABEL org.opencontainers.image.source="https://gitlab.fredouye.fr/indus/build-docker/-/blob/main/squid/Dockerfile"
LABEL org.opencontainers.image.description="Light Squid proxy image"

ENV SQUID_CONFIG_FILE /etc/squid/squid.conf
ENV TZ Europe/Paris
ENV LANG fr_FR

RUN apk add --no-cache squid squid-lang-fr \
    && mkdir -p -v /etc/squid/conf.d \
    && chown squid: /etc/squid/conf.d

VOLUME ["/var/cache/squid"]

#RUN mkdir -p -v /etc/squid/conf.d
#RUN chown squid: /etc/squid/conf.d

EXPOSE 3128/tcp

CMD ["sh", "-c", "/usr/sbin/squid -f ${SQUID_CONFIG_FILE} --foreground -z && exec /usr/sbin/squid -f ${SQUID_CONFIG_FILE} --foreground -YCd 1"]
