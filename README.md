# Custom Caddy Image with Cloudflare Plugin

This repository contains a custom Caddy image built using the Alpine version of Caddy with the Cloudflare DNS plugin.

## Features
- Based on the lightweight Alpine version of Caddy.
- Includes the Cloudflare DNS plugin for managing DNS records.

## How to Build the Image

1. Clone the repository:
   ```bash
   git clone https://github.com/HafizAhmadJamil/images.git
   cd images/caddy
   ```

2. Build the Docker image:
   ```bash
   docker build -t custom-caddy:latest --build-arg VERSION=2.6.4 .
   ```
   Replace `2.6.4` with the desired Caddy version.

## How to Use the Image

1. Run the container:
   ```bash
   docker run -d -p 80:80 -p 443:443 custom-caddy:latest
   ```

2. Use a `Caddyfile` to configure your Caddy instance. Mount it as a volume:
   ```bash
   docker run -d -p 80:80 -p 443:443 -v $(pwd)/Caddyfile:/etc/caddy/Caddyfile custom-caddy:latest
   ```

## GitHub Actions Workflow
This repository includes a GitHub Actions workflow to automatically build and push the Docker image to the GitHub Container Registry.

## Pulling the Image
Once the image is published, you can pull it using:
```bash
docker pull ghcr.io/<your-username>/custom-caddy:<commit-sha>
```
Replace `<your-username>` with your GitHub username and `<commit-sha>` with the commit hash.