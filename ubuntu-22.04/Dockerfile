FROM ubuntu:22.04

USER root
WORKDIR /root

COPY ENTRYPOINT.sh /


RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    git \
    sudo \
    lsb-release \
    curl \
    dnsutils \
    ifupdown \
    iproute2 \
    iptables \
    iputils-ping \
    net-tools \
    # mininet \
    # openvswitch-switch \
    # openvswitch-testcontroller \
    && rm -rf /var/lib/apt/lists/* \
    && touch /etc/network/interfaces \
    && chmod +x /ENTRYPOINT.sh

RUN git clone https://github.com/mininet/mininet.git && \
    mininet/util/install.sh -a && \
    rm -rf /mininet/.git

EXPOSE 6633 6653 6640

ENTRYPOINT ["/ENTRYPOINT.sh"]
