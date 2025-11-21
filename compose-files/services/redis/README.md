# Redis Service

An in-memory data structure store, used as a database, cache, and message broker.

## Features

- In-memory data storage
- Data persistence with AOF (Append Only File)
- Redis Insight web UI for monitoring and management
- High-performance caching

## Configuration

1. Copy `.env.example` to `.env` and update the variables
2. Set a secure `REDIS_PASSWORD` for production use
3. Update the `template.toml` if using template variables

## Usage

```bash
docker-compose up -d
```

## Ports

- `6379`: Redis server port (configurable via `REDIS_PORT`)
- `8001`: Redis Insight web UI port (configurable via `REDIS_INSIGHT_PORT`)

## Environment Variables

- `REDIS_PORT`: Redis server port (default: 6379)
- `REDIS_INSIGHT_PORT`: Redis Insight web UI port (default: 8001)
- `REDIS_PASSWORD`: Password for Redis authentication (optional but recommended)

## Access

- Redis CLI: `redis-cli -h localhost -p 6379`
- Redis Insight: `http://localhost:8001` or `http://${MAIN_DOMAIN}/redis`

## Volumes

- `redis_volume_data`: Persistent storage for Redis data
- `redis_insight_volume_data`: Persistent storage for Redis Insight data

