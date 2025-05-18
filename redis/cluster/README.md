# docker - redis - cluster

Redis cluster project.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

To check if it works, look in the logs of the `redis-cluster-creator` container, there should be no errors there. This container is needed only for cluster creation. After that it will be disabled. You can remove it if it is in the way.

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