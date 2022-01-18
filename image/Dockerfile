FROM alpine:3.4

RUN apk add --no-cache postfix rsyslog supervisor \
    && /usr/bin/newaliases


RUN chgrp -R 0 /root /etc && \
    chmod -R g=u /root /etc

COPY . /

EXPOSE 25

ENTRYPOINT [ "/tx-smtp-relay.sh" ]

