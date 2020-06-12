ARG DOCKER_IMAGE=debian
ARG DOCKER_IMAGE_VERSION=latest

FROM ${DOCKER_IMAGE}:${DOCKER_IMAGE_VERSION}

LABEL "alexander.nurzhanov@md.de"="Alexander Nurzhanov" \
    version="1.0" \
    description="Test Image with Python 3.7"

ARG REQUIRE_FILE='/tmp/requirements.txt'

ADD src/requirements.txt ${REQUIRE_FILE}

RUN set -eux && \
    apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    python3-dev && \
    rm -rf /var/lib/apt/lists/* && \
    echo "Set the time below host" && \
    ln -fsT /usr/share/zoneinfo/Europe/Berlin /etc/localtime && \
    pip3 install -r ${REQUIRE_FILE} && \
    ln -s /usr/bin/python3 /usr/bin/python && \
    ln -s /usr/bin/pip3 /usr/bin/pip && \
    rm ${REQUIRE_FILE}

CMD [ "python", "--version" ]