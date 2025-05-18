# docker - prometheus

Prometheus project.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

### Stop

To rollback and delete containers, run the command:

```bash
docker-compose down
```

## Description

The structure of the project is as follows:

* `docker-compose.yml` - docker-compose file;
* `.env` - file with description of variables used in `docker-compose.yml`;
* `prometheus/prometheus.yml` - configuration file for prometheus, it specifies from where to collect metrics and for which components.

## Customization

Customization is done at the `.env` file level, where you can change ports and image versions.

To add new metrics sources, in the `prometheus/prometheus.yml` file, add a section for the new source with the path to its metrics:

```yml
- job_name: 'job_name'
    static_configs:
      - targets: ['host.docker.internal:port_1','host.docker.internal:port_2']
```