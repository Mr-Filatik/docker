# docker - grafana

Grafana project.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

To test the functionality, go to [http://localhost:3000/](http://localhost:3000/) and log in with the default values of login `admin` and password `admin`.

### Add prometheus data source

To add a prometheus data resource is required:
* Go to [http://localhost:3000/connections/datasources](http://localhost:3000/connections/datasources);
* Press `Add data source`;
* Select `Prometheus`;
* Specify in `Prometheus server URL` the value of `http://host.docker.internal:9090`;
* Press `Save & Test`.

If everything went ok, you can create a dashboard. As an example (to make sure it works), you can create a dashboard and place data from the `rate(prometheus_http_requests_total[1m])` request on it.

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

Customization is done at the `.env` file level, where you can change ports and image versions.