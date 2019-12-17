FROM php:7.4-cli-alpine

#add required packages
RUN apk add gnupg ncurses

RUN  wget -O phive.phar https://phar.io/releases/phive.phar \
    && wget -O phive.phar.asc https://phar.io/releases/phive.phar.asc \
    && gpg --keyserver pool.sks-keyservers.net --recv-keys 0x9D8A98B29B2D5D79 \
    && gpg --verify phive.phar.asc phive.phar \
    && mv phive.phar /usr/local/bin/phive \
    && chmod +x /usr/local/bin/phive \
    && rm phive.phar.asc

WORKDIR /phive

#ENTRYPOINT ["/usr/bin/env"]

#CMD ["/usr/local/bin/phive"]
