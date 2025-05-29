ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:latest
FROM ${BUILD_FROM}

# Install dependencies
RUN apk add --no-cache \
    python3 \
    py3-pip \
    git \
    ffmpeg \
    libstdc++ \
    libgcc \
    openblas \
    && pip3 install insightface[all] uvicorn fastapi

# Copy app files if needed

# Create user
RUN adduser -D appuser
USER appuser

# Expose port
EXPOSE 18080

# Run server
CMD ["uvicorn", "insightface_rest.app:app", "--host", "0.0.0.0", "--port", "18080"]
