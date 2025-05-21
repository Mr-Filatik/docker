# docker - redis - standalone

One Redis instance with two replicas with UI and metrics tracking.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

### Using Redis Insight

Redis Insight is a UI for accessing Redis.

In order to connect to a radis instance you need to:

1. Go to [http://localhost:6363/](http://localhost:6363/);
2. Press `Add Redis database`;
3. Go to `Connection Settings`;
4. Type:
	1. `Database Alias`: arbitrary name
	2. `Host`: `redis-master` (`redis-slave-1` and `redis-slave-2`)
	3. `Port`: `6379`
5. Press `Add Redis database`.

### Using metrics with Prometheus

The following lines should be added to the prometheus:

```yml
- job_name: 'redis_standalone_exporter_targets'
  static_configs:
    - targets:
      - redis://host.docker.internal:6370
      - redis://host.docker.internal:6381
      - redis://host.docker.internal:6382
  metrics_path: /scrape
  relabel_configs:
    - source_labels: [__address__]
      target_label: __param_target
    - source_labels: [__param_target]
      target_label: instance
    - target_label: __address__
      replacement: host.docker.internal:9910
```

### Using metrics with Grafana

In order to observe the metrics in grafana, the following dashboard must be imported:

[Redis Exporter Dashboard](https://grafana.com/grafana/dashboards/763-redis-dashboard-for-prometheus-redis-exporter-1-x/)

### Stop

To rollback and delete containers, run the command:

```bash
docker-compose down
```

If you want to recreate the cluster again, you must delete the `data` folder. The cluster will then be created from scratch.

## Description

The structure of the project is as follows:

* `docker-compose.yml` - docker-compose file;
* `.env` - file with description of variables used in `docker-compose.yml`.

## Customization

Customization is done at the `.env` file level, where you can change ports and image versions.