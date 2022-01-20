FROM alpine:3.4

RUN apk add --no-cache postfix rsyslog supervisor \
    && /usr/bin/newaliases

COPY . /

EXPOSE 25

ENTRYPOINT [ "/tx-smtp-relay.sh" ]

