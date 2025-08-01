# Docker Compose Services Collection

A curated collection of Docker Compose configurations for various applications and services, organized for easy deployment and management.

## Available Services

### Analytics & Business Intelligence
- **qdrant** - Vector database for ML applications
- **influx_db** - Time series database
- **timescale_db** - PostgreSQL extension for time-series data

### Business & Productivity
- **appsmith** - Low-code platform for building internal tools
- **n8n** - Workflow automation platform
- **odoo** - Enterprise resource planning (ERP) software
- **plane** - Project management platform
- **twentycrm** - Modern CRM platform

### AI & Machine Learning
- **ollama** - Run large language models locally
- **langflow** - Visual framework for building LangChain applications

### Authentication & Security
- **keycloak** - Identity and access management
- **zitadel** - Identity infrastructure platform

### Content & Media
- **calibre-web** - Web-based e-book library manager
- **AFFiNE** - Knowledge management and collaboration platform

### Storage & Databases
- **postgres_db** - PostgreSQL database
- **redis** - In-memory data structure store
- **minio** - S3-compatible object storage

### Trading & Finance
- **jesse.trade** - Cryptocurrency trading bot
- **quantrocket** - Quantitative trading platform
- **mt5** - MetaTrader 5 trading platform
- **metatrader5_docker** - Dockerized MetaTrader 5 setup

### Remote Access & Virtualization
- **kasm** - Container-based remote desktop platform

## Quick Start

1. Navigate to the desired service directory:
   ```bash
   cd <service-name>/
   ```

2. Start the service:
   ```bash
   docker-compose up -d
   ```

3. Check service status:
   ```bash
   docker-compose ps
   ```

4. View logs:
   ```bash
   docker-compose logs -f
   ```

5. Stop the service:
   ```bash
   docker-compose down
   ```

## Prerequisites

- Docker Engine 20.10+
- Docker Compose v2.0+
- Sufficient disk space for containers and volumes
- Network ports available (check individual service configurations)

## Configuration

Each service directory contains:
- `docker-compose.yml` - Main configuration file
- Environment-specific files (if applicable)
- README with service-specific instructions (where available)

## Management Commands

### Start all services
```bash
find . -name "docker-compose.yml" -execdir docker-compose up -d \;
```

### Stop all services
```bash
find . -name "docker-compose.yml" -execdir docker-compose down \;
```

### Update all services
```bash
find . -name "docker-compose.yml" -execdir docker-compose pull \;
find . -name "docker-compose.yml" -execdir docker-compose up -d \;
```

### Check status of all services
```bash
for dir in */; do
  if [ -f "$dir/docker-compose.yml" ]; then
    echo "=== $dir ==="
    (cd "$dir" && docker-compose ps)
  fi
done
```

## Troubleshooting

### Common Issues

1. **Port conflicts**: Check if ports are already in use
   ```bash
   netstat -tulpn | grep <port>
   ```

2. **Permission issues**: Ensure proper file permissions
   ```bash
   sudo chown -R $USER:$USER <service-directory>
   ```

3. **Network issues**: Reset Docker networks
   ```bash
   docker network prune
   ```

4. **Volume issues**: Clean up unused volumes
   ```bash
   docker volume prune
   ```

### Logs and Debugging

View logs for a specific service:
```bash
cd <service-directory>
docker-compose logs -f [service-name]
```

## Security Considerations

- Review default passwords and credentials
- Configure proper firewall rules
- Use environment variables for sensitive data
- Keep containers updated regularly
- Limit network exposure when possible

## Contributing

When adding new services:
1. Create a dedicated directory
2. Include a proper `docker-compose.yml`
3. Update this README
4. Test the configuration
5. Document any special requirements

## License

Individual services may have their own licensing terms. Please refer to each service's documentation for specific license information.