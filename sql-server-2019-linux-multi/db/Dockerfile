FROM mcr.microsoft.com/mssql/server:2019-latest
LABEL maintainer "André Raabe <andre.raabe@gmail.com>"

ENV SA_PASSWORD=P@ssw0rd
ENV MSSQL_PID=Developer
ENV ACCEPT_EULA=Y
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

USER root

COPY ./*.sh /
COPY ./*.sql /
COPY ./mssql.conf /tmp/mssql.conf

RUN set -ex \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
        coreutils \
        inetutils-ping \
        less \
        net-tools \
        tree \
    && apt-get autoclean -y \
    && rm -rf /var/lib/apt/lists/* \
    && chmod +x /*.sh

USER mssql

CMD /bin/bash /entrypoint.sh

