# Overnites

## Docker containers
All the containers run on their own seperated network. The network is configured in a bridge configuration

### Usage
We have 2 docker compose configuration files, 1 for developing and 1 for production.

#### Production
##### Start
```bash
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build 
```


#### Development
##### Start
```bash
docker-compose up --build -d
```

##### Stop
```bash
docker-compose down
```

#### General
##### Remove
Remove docker containers, remember to shutdown first.
```bash
docker-compose rm
```

##### Prune
Remove all unused container volumes.
```bash
docker volume prune
```

##### Logs
```bash
docker-compose logs -f astro
```
```bash
docker-compose logs -f fastify
```
```bash
docker-compose logs -f nginx
```
```bash
docker-compose logs -f mariadb
```
```bash
docker-compose logs -f redis
```

##### SSH
```bash
docker-compose exec astro /bin/bash
```
```bash
docker-compose exec fastify /bin/bash
```
```bash
docker-compose exec nginx /bin/bash
```
```bash
docker-compose exec mariadb /bin/bash
```
```bash
docker-compose exec redis /bin/bash
```

### mariadb
This container is running our mariadb server.  

Port 3306 is exposed to the host.  

### redis
The container running our redis caching server.  

Port 6379 is exposed to the host.

### nginx
This container is acting as a proxy into our nodejs server.  

Port 80 and 443 is exposed to the host.  

### Astro
The container running our Astro frontend.  

No ports are exposed to the host.  
Astro exposes port 3000 to the local docker network, this port will then be tunneled to port 80 & 443 via the nginx container.  

### Fastify
The container running our Fastify backend.  

No ports are exposed to the host.  
Fastify exposes port 3000 to the local docker network, this port will then be tunneled to port 80 & 443 via the nginx container.  