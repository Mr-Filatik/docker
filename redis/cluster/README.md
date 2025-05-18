# docker - redis - cluster

Redis cluster project with separate metrics exporters for each master node and multi-exporters for slave nodes.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

To check if it works, look in the logs of the `redis-cluster-creator` container, there should be no errors there. This container is needed only for cluster creation. After that it will be disabled. You can remove it if it is in the way.

### Using

The following lines should be added to the prometheus.

Exporter for each master node:

```yml
- job_name: 'redis_exporter'
  static_configs:
    - targets:
      - host.docker.internal:9911
      - host.docker.internal:9912
      - host.docker.internal:9913
```

Exporter for all slave nodes:

```yml
- job_name: 'redis_exporter_targets'
  static_configs:
    - targets:
      - redis://host.docker.internal:6381
      - redis://host.docker.internal:6382
      - redis://host.docker.internal:6383
      - redis://host.docker.internal:6384
      - redis://host.docker.internal:6385
      - redis://host.docker.internal:6386
  metrics_path: /scrape
  relabel_configs:
    - source_labels: [__address__]
      target_label: __param_target
    - source_labels: [__param_target]
      target_label: instance
    - target_label: __address__
      replacement: host.docker.internal:9920
```

### Stop

To rollback and delete containers, run the command:

```bash
docker-compose down
```

Additionally, if you want to recreate the cluster, you must delete the `data` folder. After that, the cluster will be recreated.

## Description

The structure of the project is as follows:

* `docker-compose.yml` - docker-compose file;
* `.env` - file with description of variables used in `docker-compose.yml`.

## Customization

Customization is done at the `.env` file level, where you can change ports and image versions.