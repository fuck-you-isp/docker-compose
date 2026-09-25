# docker-compose
Single compose file to get stack up and running

## Quick start

Requires Docker with the Compose plugin. On Windows, use Docker Desktop with the WSL2 backend (WSL1 is not supported).

```bash
curl -fsSLO https://raw.githubusercontent.com/fuck-you-isp/docker-compose/main/docker-compose.yml
docker compose up -d
```

Grafana is available locally at http://localhost:3000 (login: `admin` / `grafana`).

## Get the public Cloudflare URL

The `cloudflared` service opens a Cloudflare quick tunnel to Grafana. Its public URL is in the container logs:

```bash
docker logs cloudflared
```

Look for the `https://<random-words>.trycloudflare.com` address in the box that says *Your quick Tunnel has been created!* If it's not there yet, wait a few seconds and run the command again.

The URL is random and changes every time the `cloudflared` container restarts, so run the command again after a restart or reboot.

> **Warning:** the tunnel makes Grafana reachable from the internet. Change the default `admin` / `grafana` credentials before sharing the URL.

## Stop the stack

```bash
docker compose down
```
