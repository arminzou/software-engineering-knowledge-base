# Software Engineering Knowledge Base

A personal collection of software engineering knowledge, learning notes, and resources.

## Setup & Deployment

### Local Development
```bash
pip install mkdocs-material mkdocs-minify-plugin
mkdocs serve
```

### GitHub Actions Deployment
This repository is configured to automatically deploy to a Docker VM via SSH when changes are pushed to the main branch.

#### Required GitHub Secrets
- `SSH_PRIVATE_KEY`: Private SSH key for VM access
- `VM_HOST`: Docker VM hostname or IP address  
- `VM_USER`: SSH username for the VM
- `VM_PATH`: Deployment path on the VM (e.g., `/var/www/mkdocs`)

#### Docker VM Setup
1. Generate SSH key pair:
   ```bash
   ssh-keygen -t rsa -b 4096 -C "github-actions"
   ```

2. Add public key to VM's `~/.ssh/authorized_keys`

3. Add private key to GitHub repository secrets

4. On the VM, create deployment directory:
   ```bash
   mkdir -p /var/www/mkdocs
   cd /var/www/mkdocs
   ```

5. Copy `docker-compose.yml` and `nginx.conf` to the VM

6. Start the Docker container:
   ```bash
   docker-compose up -d
   ```

The site will be available at your VM's IP address on port 80.

## Project Structure
- `docs/` - Documentation source files
- `site/` - Generated static site (created by `mkdocs build`)
- `.github/workflows/` - GitHub Actions workflows
- `docker-compose.yml` - Docker configuration for deployment
- `nginx.conf` - Nginx configuration for serving the site