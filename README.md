# PHP Docker Development Images

This repository stores Docker images for PHP to avoid rewriting the same Dockerfile for every project.

## Features

- **Multi-Architecture Builds:** Images are built for both `linux/amd64` (standard Linux) and `linux/arm64` (Apple Silicon).
- **Automated Workflow:** A GitHub Actions workflow automatically builds and pushes images to the GitHub Container Registry (GHCR) on every push to the `main` branch.
- **Cleanup:** The workflow keeps the registry clean by removing any tags other than `latest` after a successful push.

## Available Images

The following images are built and pushed to GHCR:

- `ghcr.io/<your-github-username>/php8.4-fpm:latest`
- `ghcr.io/<your-github-username>/php8.4-fpm-xdebug:latest`

Replace `<your-github-username>` with your actual GitHub username or organization name.
