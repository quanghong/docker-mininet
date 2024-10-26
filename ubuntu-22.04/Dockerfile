FROM ubuntu:22.04

USER root
WORKDIR /root

COPY ENTRYPOINT.sh /

# Update and install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    git \
    sudo \
    lsb-release \
    iputils-ping \
    # curl \
    # dnsutils \
    # ifupdown \
    # iproute2 \
    # iptables \
    # net-tools \
    # mininet \
    # openvswitch-switch \
    # openvswitch-testcontroller \
    && rm -rf /var/lib/apt/lists/* \
    # && touch /etc/network/interfaces \
    && chmod +x /ENTRYPOINT.sh

# Install Mininet from GitHub
RUN git clone https://github.com/mininet/mininet.git && \
    mininet/util/install.sh -a && \
    rm -rf /mininet/.git

EXPOSE 6633 6653 6640

ENTRYPOINT ["/ENTRYPOINT.sh"]
