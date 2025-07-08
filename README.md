# rosetta_monitoring
## add ports to .env file (eg `.env.docker-compose`)
```
## Monitoring variables
PROMETHEUS_PORT=9090
GRAFANA_PORT=3000
POSTGRESQL_EXPORTER_PORT=9187
```
## run docker compose
```
docker compose --env-file ../.env.docker-compose -f -f docker-compose-monitor.yaml  -d 
```
