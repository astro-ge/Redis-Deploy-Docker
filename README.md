# Redis Docker Deployment

Redis 7 with AOF persistence, deployed via Docker Compose.

## Quick Start

```bash
# 1. Copy and configure environment variables
cp .env.example .env
vim .env  # Set REDIS_PASSWORD

# 2. Start
docker compose up -d

# 3. Check status
docker compose ps
docker compose logs -f redis
```

## Connection

- **URL**: `redis://:your_password@<host>:6379/0`
- **Port**: 6379

## Commands

```bash
# Stop
docker compose down

# Stop and remove data
docker compose down -v

# Restart
docker compose restart

# View logs
docker compose logs -f redis

# Connect to Redis CLI
docker exec -it redis redis-cli -a your_password

# Check memory usage
docker exec redis redis-cli -a your_password INFO memory

# Monitor commands in real time
docker exec redis redis-cli -a your_password MONITOR

# Check connected clients
docker exec redis redis-cli -a your_password CLIENT LIST

# Flush all data (careful!)
docker exec redis redis-cli -a your_password FLUSHALL
```

## Configuration

- `docker-compose.yml` — service definition, ports, memory, persistence
- `.env` — password, port, memory limits
