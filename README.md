# Switch Testbed Load Balancer – Production Config Bundle

## Files
- `docker-compose.yml`: uses Docker Hub images and mounts config/secrets.
- `config/backend.env.example`: set `API_BEARER_TOKEN` and copy to `config/backend.env` (gitignored).
- `config/frontend.env.example`: set `VITE_API_BASE_URL` and copy to `config/frontend.env` (gitignored).
- `config/base/device.yaml`: sample inventory; replace with your real devices.
- `config/secrets/credentials.yaml.example`: copy to `config/secrets/credentials.yaml` and fill SSH creds (gitignored).
- `.gitignore`: ignores real env files and secrets.

## Setup
```bash
cp config/backend.env.example config/backend.env
cp config/frontend.env.example config/frontend.env
cp config/secrets/credentials.yaml.example config/secrets/credentials.yaml
# edit the three files above to real values
nano config/base/device.yaml
```

## Run (pull latest images)
```bash
docker compose pull
docker compose up -d
# or to rebuild network changes:
docker compose up -d --remove-orphans
```

The compose exposes backend on `8000` and frontend on `8080`. Healthcheck gates frontend startup.
