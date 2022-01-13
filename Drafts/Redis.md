## Steps to run Redis in Docker

## Volume

```docker
docker volume create redis-data

```

## Running

```docker
docker run --name redis -d -v redis-data:/data -p 6379:6379 -e REDIS_PASSWORD=redis-password --restart always \
    redis redis-server --appendonly yes --requirepass ${REDIS_PASSWORD}

```

## Remove

```docker
docker rm -f redis

docker volume rm redis-data

```