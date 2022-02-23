# mosdns-cn docker

Docker build for mosdns-cn

https://hub.docker.com/r/xuss/mosdns-cn

## how to use

docker-compose.yaml

```yaml
mosdns-cn:
    image: xuss/mosdns-cn:latest
    container_name: mosdns-cn
    volumes:
      - ./conf/mosdns-cn:/etc/mosdns-cn
    restart: unless-stopped
    network_mode: "host"
    logging:
      driver: "journald"
```

in directory `./conf/mosdns-cn`

```sh
config.yaml  geoip.dat  geosite.dat
```

download `geoip.dat` and `geosite.dat` from [v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)

my config.yaml

```yaml
server_addr: ":5300"
cache_size: 0
lazy_cache_ttl: 0
lazy_cache_reply_ttl: 0
redis_cache: ""
min_ttl: 0
max_ttl: 0
hosts: []
arbitrary: []
blacklist_domain: []
insecure: false
ca: []
debug: false
log_file: ""
upstream: []
local_upstream: ["119.29.29.29"]
local_ip: ["geoip.dat:cn"]
local_domain: ["geosite.dat:cn"]
local_latency: 50
remote_upstream: ["8.8.8.8"]
remote_domain: ["geosite.dat:geolocation-!cn"]
working_dir: "/etc/mosdns-cn"
cd2exe: false
```
Now you can use mosdns-cn in port 5300
