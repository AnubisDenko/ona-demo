# ONA Development Dockerfile
# Base image with Gradle and JDK 17
#FROM gradle:8.7.0-jdk17
#FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04
FROM mcr.microsoft.com/devcontainers/java:dev-21

# Install Docker CLI and Docker daemon
USER root
RUN systemctl enable docker
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        docker.io \
        docker-compose \
        git \
        curl \
        redis-tools \
        unzip && \
    rm -rf /var/lib/apt/lists/*

RUN usermod -aG docker vscode

# Set up Docker-in-Docker entrypoint and other env variables
ENV DOCKER_HOST=unix:///var/run/docker.sock \
    JAVA_HOME=/usr/lib/jvm/msopenjdk-current


# Expose Docker socket
VOLUME /var/run/docker.sock

# Set working directory
WORKDIR /workspace
USER vscode

# Entrypoint for interactive development
CMD ["bash"]

