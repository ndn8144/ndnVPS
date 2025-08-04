FROM ubuntu:22.04

# Cập nhật hệ thống và cài gói cơ bản
RUN apt-get update && apt-get install -y \
    curl wget git sudo locales vim \
    gnupg lsb-release software-properties-common \
    ca-certificates apt-transport-https gnupg-agent \
    build-essential unzip bash-completion \
    python3 python3-pip \
    docker.io docker-compose \
    && rm -rf /var/lib/apt/lists/*

# Thiết lập locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# Tạo user không phải root
ARG USERNAME=dev
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/nopasswd \
    && chmod 0440 /etc/sudoers.d/nopasswd

USER $USERNAME
WORKDIR /home/$USERNAME

# Cài Node.js (LTS)
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - \
    && sudo apt-get install -y nodejs

# Cài Go (phiên bản mới)
ENV GO_VERSION=1.22.0
RUN wget https://go.dev/dl/go$GO_VERSION.linux-amd64.tar.gz && \
    sudo rm -rf /usr/local/go && \
    sudo tar -C /usr/local -xzf go$GO_VERSION.linux-amd64.tar.gz && \
    rm go$GO_VERSION.linux-amd64.tar.gz
ENV PATH="/usr/local/go/bin:$PATH"

# Cài Rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENV PATH="/home/$USERNAME/.cargo/bin:$PATH"

# Kiểm tra phiên bản
RUN node -v && npm -v && go version && rustc --version && cargo --version
