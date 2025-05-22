# docker - clickhouse - simple

A simple one instance ClickHouse with metrics tracking.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

### Using metrics in Grafana with Prometheus



### Using metrics in Grafana without Prometheus

Tracking metrics in Grafana without Prometheus requires:

1. Install `ClickHouse` plugin;
2. Add a new `ClickHouse` datasource;
3. Specify the host.docker.internal server and port 8123;
4. Select the HTTP protocol;
5. Specify the login default and password password.

Next, you need to import dashboards or create your own.

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

Configuration is done at the `.env` file level, where you can change ports, image versions, etc.

Create a file for your environment, for example `.env.dev` based on `.env`. And run the command:

```bash
docker-compose --env-file .env.dev up -d
```

Files that are added to `.gitignore`: `.env.dev`, `.env.test`, `.env.prod`.


