
FROM debian:latest

WORKDIR /opt

RUN apt-get update && \
  apt-get upgrade -y && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y \
  git \
  python-dev \
  python-pip \
  screen \
  p7zip-full \
  libjpeg-dev \
  zlib1g-dev \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg2 \
  software-properties-common

RUN curl -fsSL https://www.mongodb.org/static/pgp/server-4.2.asc | apt-key add -
RUN echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.2 main" | tee /etc/apt/sources.list.d/mongodb-org-4.2.list

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/debian \
    $(lsb_release -cs) \
    stable"

RUN apt-get update && apt-get install -y \
    docker-ce \
    docker-ce-cli \
    containerd.io

RUN apt-get update && apt-get install -y \
    mongodb-org


RUN pip install virtualenv && \
    git clone https://github.com/certsocietegenerale/fame

ENTRYPOINT ["/opt/fame/docker/launch.sh"]
EXPOSE 4200
