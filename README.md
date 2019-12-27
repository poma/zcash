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

## Check hashrate

    time ~/zcash/src/zcash-cli zcbenchmark solveequihash 10
    
    
    time solveequihash NUM_ITERS [NUM_THREADS]

The result will be something like

    real    1m15.879s
    user    0m0.000s
    sys     0m0.004s

where the first number is the real time taken. Divide 10 by this value (converted into seconds) and you have your hashrate in hashes per second. Of course the advantage to this method is that you can easily run 100 or 1000 loops to average out the run times.

- see [How do i check my hashrate?](https://forum.z.cash/t/how-do-i-check-my-hashrate/672/11)
- https://forum.z.cash/t/how-to-check-mining-hashrate-with-zcash-built-in-miner/2810
- https://forum.z.cash/t/monitor-zcashd-hash-rate-in-daemon-mode/4531/12
- https://www.cryptocompare.com/mining/calculator/zec
- https://steemit.com/mining/@takenbtc/how-mining-zcash

## Releases

Will be the same as **Zcash** releases: https://github.com/zcash/zcash/releases