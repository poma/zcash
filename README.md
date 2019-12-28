# Zcash full node [![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/poma/zcash.svg)](https://hub.docker.com/r/poma/zcash/builds)

## Download zcash parameters

    docker run --rm -v /data/zcash/.zcash-params:/root/.zcash-params:rw --entrypoint zcash-fetch-params poma/zcash
    
## Run

    docker run -d -v /data/zcash/.zcash-params:/root/.zcash-params:ro -v /data/zcash/.zcash:/root/.zcash:rw -p 8232:8232 poma/zcash

## Example docker-compose.yml

```yaml
version: '2'

services:
  zcash:
    image: poma/zcash
    restart: always
    ports:
      - 8232:8232
    volumes: 
      - /data/zcash/.zcash-params:/root/.zcash-params:ro
      - /data/zcash/.zcash:/root/.zcash:rw
```

## Releases

Will be the same as **Zcash** releases: https://github.com/zcash/zcash/releases
