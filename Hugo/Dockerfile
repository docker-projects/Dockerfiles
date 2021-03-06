#
# Docker image for
#
# Hugo
#
#
# Create:
#
# sudo docker build --rm -t akaer/hugo . 2>&1 |tee docker_build.log
#
# Run:
#
#  sudo docker run --rm=true -it \
#   --name hugo \
#   -v /etc/localtime:/etc/localtime:ro \
#   -v $(pwd):/data \
#   akaer/hugo
#
#
# Sample:
#
# docker run --rm=true -it -v $(pwd):/data -p 1313:1313 --user="$(id -u):$(id -g)" akaer/hugo new site samplesite
# docker run --rm=true -it -v $(pwd):/data -p 1313:1313 --user="$(id -u):$(id -g)" akaer/hugo new post/testpost.md
# docker run --rm=true -it -p 1313:1313 -v $(pwd):/data --user="$(id -u):$(id -g)" akaer/hugo server --bind 0.0.0.0 --buildDrafts
#

FROM akaer/base
LABEL maintainer "André Raabe <andre.raabe@gmail.com>"

ENV HUGO_VERSION 0.32.4

RUN set -ex \
    && apk update \
    && apk add --no-cache \
        curl \
    && rm -rf /var/cache/apk/* \
    && curl -sSL \
        https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_Linux-64bit.tar.gz \
        -o /tmp/hugo_${HUGO_VERSION}_linux-64bit.tgz \
    && cd /tmp/ \
    && tar -vxzf hugo_${HUGO_VERSION}_linux-64bit.tgz \
    && mv hugo /usr/bin/hugo \
    && rm -f hugo_${HUGO_VERSION}_linux-64bit.tgz README.md LICENSE.md \
    && rm -rf hugo_${HUGO_VERSION}_linux_amd64

VOLUME [ "/data" ]
WORKDIR /data
EXPOSE 1313
ENTRYPOINT [ "hugo" ]
CMD [ "version" ]

