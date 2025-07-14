FROM python:3.11-alpine

# Set metadata
LABEL maintainer="Python UV Dev Container"
LABEL description="Minimal Alpine-based Python development container with uv and ruff"

# Set environment variables
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    UV_CACHE_DIR=/tmp/uv-cache \
    PATH="/root/.local/bin:$PATH"

# Install system dependencies
RUN apk add --no-cache \
    git \
    curl \
    bash \
    build-base \
    libffi-dev \
    openssl-dev \
    && rm -rf /var/cache/apk/*

# Install uv and ruff
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir uv ruff

# Create cache directory
RUN mkdir -p /tmp/uv-cache

# Verify installations
RUN uv --version && ruff --version

# Set working directory
WORKDIR /workspaces

# Default command
CMD ["/bin/bash"]
