FROM ubuntu:24.04

ARG DEBIAN_FRONTEND=noninteractive

# Install development tools, Node.js, and Rust dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    curl ca-certificates gnupg git build-essential sudo \
    pkg-config libssl-dev && \
    curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y --no-install-recommends nodejs && \
    rm -rf /var/lib/apt/lists/*

# Ubuntu 24.04 ships with user 'ubuntu' already created with UID 1000.
# Give ubuntu passwordless sudo
RUN echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER ubuntu

# Install Rust for ubuntu user
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/home/ubuntu/.cargo/bin:/home/ubuntu/.local/bin:${PATH}"

WORKDIR /workspace
