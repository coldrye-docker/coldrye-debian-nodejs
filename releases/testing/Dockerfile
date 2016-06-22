FROM coldrye/debian-tini:0-9-0-testing-latest

MAINTAINER Carsten Klein <trancesilken@gmail.com>

ARG NODE_VERSION=4.x

RUN set -x \
    && export APT_LISTCHANGES_FRONTEND=none \
    && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION} | bash - \
    && apt-get -q -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install nodejs \
    && ln -f -s /usr/bin/nodejs /usr/bin/node \
    && npm -g install npm \
    && apt-get clean \
    && rm -Rf /var/lib/apt/lists/* 2>/dev/null

