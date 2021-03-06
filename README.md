# Docker EFK(Elasticsearch, Fluentd, Kibana)

EFK setup with docker, docker-compose.

## Requirements

- docker
- docker-compose

## Usege

Using docker-machine

```sh
docker-machine create -d virtualbox dev
eval "$(docker-machine env dev)"
```

```sh
docker-compose up
```

Use Background

```sh
docker-compose up -d
```

```sh
docker-compose ps
          Name                         Command               State                Ports
-----------------------------------------------------------------------------------------------------
dockerefk_elasticsearch_1   /docker-entrypoint.sh elas ...   Up      0.0.0.0:9200->9200/tcp, 9300/tcp
dockerefk_fluentd_1         sh -c /tmp/entrypoint.sh         Up      0.0.0.0:24224->24224/tcp
dockerefk_kibana_1          /docker-entrypoint.sh /tmp ...   Up      0.0.0.0:5601->5601/tcp
dockerefk_nginx_1           sh -c /tmp/entrypoint.sh         Up      443/tcp, 0.0.0.0:80->80/tcp
dockerefk_node_app_1        sh -c /tmp/entrypoint.sh         Up      0.0.0.0:8080->8080/tcp
```

```sh
# open kibana
open http://localhot:5601

# if use docker-machine
open http://"$(docker-machine ip dev)":5601
```
For ElasticSearch need to install the following two plugins.
bin/plugin install license
bin/plugin install marvel-agent

If you use docker-toolbox, localhost is docker-machine ip.


Build and run fluentd
docker build ./fluentd
docker run -d -p 24224:24224 -v /home/data/mnt/docker/containers:/var/lib/docker/containers fluent/fluentd:latest
