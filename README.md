# Gaming Platform Infrastructure

Quick guide to run and manage the Gaming Platform services.

## Starting Services

```bash
# Start all services
docker-compose -f docker-compose-full.yml up -d

# Check services status
docker-compose -f docker-compose-full.yml ps
```

## Kafka Topics

The following topics are automatically created on startup:
- `game-events`: Game events and invites (3 partitions)
- `social-events`: Friend requests and social updates (3 partitions)
- `user-notifications`: General user notifications (3 partitions)

## Accessing Services

- Kafka UI: http://localhost:8080
  - View topics and messages
  - Monitor brokers
  - Create additional topics

- Game Service: http://localhost:8081
- Social Service: http://localhost:8082
- Notification Service: http://localhost:8083

## Default Users Configuration

The notification service comes with pre-configured users:

- playerId: `1`: Game notifications enabled, Social disabled
- playerId: `2`: Game notifications disabled, Social enabled
- playerId: `3`: All notifications disabled
- Any other player have all notification enabled

These users can be used for testing notification preferences.

## Testing with Postman

Import the Gaming Platform Postman collection:
- File: `Gaming-Platform.postman_collection.json`
- Contains all API endpoints for testing
- Pre-configured environments

## Stopping Services

```bash
docker-compose -f docker-compose-full.yml down
```

## Troubleshooting

If services are unhealthy:
```bash
# Check service logs
docker logs notification-service
docker logs game-service
docker logs social-service
docker logs kafka-init    # Check topic creation status
```
