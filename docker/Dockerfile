FROM php:7.4-cli-alpine

ARG USER_ID=1000
ARG GROUP_ID=1000

#add required packages
RUN set -xe \
 && apk add gnupg ncurses \
 && apk --no-cache add --virtual .build-deps  shadow \
 && groupadd -g $GROUP_ID -o -f www-data \
 && usermod -u $USER_ID www-data --home /phive \
 && apk del .build-deps

RUN  wget -O phive.phar https://phar.io/releases/phive.phar \
    && wget -O phive.phar.asc https://phar.io/releases/phive.phar.asc \
    && gpg --keyserver pool.sks-keyservers.net --recv-keys 0x9D8A98B29B2D5D79 \
    && gpg --verify phive.phar.asc phive.phar \
    && mv phive.phar /usr/local/bin/phive \
    && chmod +x /usr/local/bin/phive \
    && rm phive.phar.asc

RUN mkdir /phive && chown -R www-data:www-data /phive

WORKDIR /phive

USER www-data

ENTRYPOINT ["/usr/local/bin/phive"]
