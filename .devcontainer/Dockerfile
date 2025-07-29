# Enable auto-activation of the 'base' env in Dockerfile runs
ARG MAMBA_DOCKERFILE_ACTIVATE=1

FROM mambaorg/micromamba:1.5.3

# Copy env specification & install everything into `base`
COPY environment.yml /tmp/environment.yml
RUN micromamba install --yes -n base -f /tmp/environment.yml \
    && micromamba clean --all --yes

# Ensure conda-installed Python is on PATH
ENV PATH=/opt/conda/bin:$PATH

# Set the workspace
WORKDIR /workspace

# Switch to root to install system packages and set up users
USER root

# Install sudo and other system requirements
RUN apt-get update \
  && apt-get install -y \
    sudo \
    cmake \
    build-essential \
    libcurl4-openssl-dev \
    libxml2-dev \
    libssl-dev \
    libxt6 \
    libgsl-dev \
    libnode-dev \
    libnlopt-dev \
    libmagick++-dev \
    sqlite3 \
    curl \
    nano \
    neofetch \
    tmux \
    git \
    gh \
    fonts-roboto \
    fonts-open-sans \
    fonts-texgyre \
    fonts-firacode \
    fonts-dejavu \
    fonts-dejavu-core \
    fonts-dejavu-extra \
  && rm -rf /var/lib/apt/lists/*

# Create vscode user and set up sudo access
RUN useradd -m -s /bin/bash vscode \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/vscode \
    && chmod 0440 /etc/sudoers.d/vscode \
    && chown -R vscode:vscode /workspace \
    && chown -R vscode:vscode /opt/conda

# Switch to vscode user
USER vscode
