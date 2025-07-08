# rosetta_monitoring
## add ports to .env file (eg `.env.docker-compose`)
```
## Monitoring variables
PROMETHEUS_PORT=9090
GRAFANA_PORT=3000
POSTGRESQL_EXPORTER_PORT=9187
```
## adding dependencies to  pom.xml files:
/home/integration/git/cardano-rosetta-java/yaci-indexer/pom.xml

/home/integration/git/cardano-rosetta-java/api/pom.xml
```
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <dependency>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-registry-prometheus</artifactId>
        </dependency>
```

## change config files   
/home/integration/git/cardano-rosetta-java/yaci-indexer/src/main/resources/application.properties

/home/integration/git/cardano-rosetta-java/api/src/main/resources/config/application.yaml
```
management.endpoints.web.exposure.include=health,info,prometheus
```

## change cnode config files 
/home/integration/git/cardano-rosetta-java/config/mainnet/config.json

/home/integration/git/cardano-rosetta-java/config/preprod/config.json

/home/integration/git/cardano-rosetta-java/config/preview/config.json

```
 "hasPrometheus": [
    "0.0.0.0",
    12798
  ],
```


## run docker compose
```
docker compose --env-file ../.env.docker-compose  -f docker-compose-monitor.yaml up -d 
```
