# Software Engineering Knowledge Base

A personal collection of software engineering knowledge, learning notes, and resources.

## Setup & Deployment

### Local Development

```bash
pip install mkdocs-material mkdocs-minify-plugin
mkdocs serve
```

### GitHub Actions Deployment

This repository is configured to automatically deploy via GitHub Actions when changes are pushed to the main branch, using a self-hosted runner on the Docker VM.

1. On the VM, create deployment directory:

   ```bash
   mkdir -p ~/docker/mkdocs/software-engineering-kb
   ```

2. Copy `compose.yaml` to the VM

3. Start the Docker container:

   ```bash
   docker compose up -d
   ```

## Project Structure

- `docs/` - Documentation source files
- `site/` - Generated static site (created by `mkdocs build`)
- `.github/workflows/` - GitHub Actions workflows
- `compose.yaml` - Docker configuration for deployment
