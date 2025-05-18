# docker - kafka

Kafka project with three brokers configured.

## Using

### Launch

Open the console at the file path and run the command:

```bash
docker-compose up -d
```

To test the functionality, go to [http://localhost:8092/ui/clusters/dev/brokers](http://localhost:8092/ui/clusters/dev/brokers) and make sure the cluster `dev` and all brokers are available.

### Stop

To rollback and delete containers, run the command:

```bash
docker-compose down
```

## Description

The structure of the project is as follows:

* `docker-compose.yml` - docker-compose file;
* `.env` - file with description of variables used in `docker-compose.yml`;
* `jmx-exporter/kafka-broker.yml` - configuration file for Prometheus JMX Exporter, which is used to collect metrics from Java applications via JMX (Java Management Extensions);
* `jmx-exporter/jmx_prometheus_javaagent-1.3.0.jar` - an application that connects to Java applications (e.g. Apache Kafka, ZooKeeper, etc.) and exports metrics in Prometheus format. Download the latest version by clicking [here](https://github.com/prometheus/jmx_exporter/releases).

## Customization

Customization is done at the `.env` file level, where you can change ports and image versions.
