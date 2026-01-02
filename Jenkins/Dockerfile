FROM jenkins/inbound-agent:latest

USER root

# Install minimal dependencies
RUN apt-get update && apt-get install -y \
    curl \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Install Trivy (binary)
RUN curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh \
    | sh -s -- -b /usr/local/bin

# Set Trivy cache directory
ENV TRIVY_CACHE_DIR=/tmp/trivy-cache

RUN mkdir -p /tmp/trivy-cache && chmod 777 /tmp/trivy-cache

# Verify installation
RUN trivy --version

USER jenkins
