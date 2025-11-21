# Nginx Service

A lightweight and high-performance web server and reverse proxy.

## Features

- HTTP/HTTPS web server
- Reverse proxy capabilities
- Load balancing
- SSL/TLS termination

## Configuration

1. Copy `.env.example` to `.env` and update the variables
2. Update the `template.toml` if using template variables
3. Customize nginx configuration in the mounted volume

## Usage

```bash
docker-compose up -d
```

## Ports

- `80`: HTTP port (configurable via `NGINX_PORT`)

## Environment Variables

- `NGINX_HOST`: Domain name for the nginx server
- `NGINX_PORT`: Port number for HTTP (default: 80)

