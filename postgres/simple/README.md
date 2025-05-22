# docker - postgres - simple

Single instance Postgres database.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

### Using metrics in Grafana with Prometheus



### Using metrics in Grafana without Prometheus

Tracking metrics in Grafana without Prometheus requires:

1. Install `PostgreSQL` plugin;
2. Add a new `PostgreSQL` datasource;
3. Specify in `Host URL` host.docker.internal:5432;
4. Specify in `Database name` default;
5. Specify the login default and password password;
6. Disable `TLS/SSL Mode`.

Next, you need to import dashboards or create your own.

### Stop

To rollback and delete containers, run the command:

```bash
docker-compose down
```

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