Process Services Docker Library
================================

A small collections of examples on how to use process services for development purposes.

We aim to support 3 main environments:
 - Compose
   - [README](./docker-compose/README.md)
   - [Process Services only](./docker-compose/ps-only/docker-compose.yml)
   - [Process Services + Postgres](./docker-compose/ps-postgres/docker-compose.yml)
   - [Process Services + Postgres + ElasticSearch](./docker-compose/ps-postgres-es/docker-compose.yml)
 - Kubernetes
   - TBD
 - ECS
   - TBD


## Configuration

The system provides two-way support for importing your own configuration.

### Updating the default properties

If you want to change the default admin account details or change details of the CORS, CSRF or database configuration, you can override the following environment variables in any orchestration system.

  - `ACTIVITI_LICENSE_MULTI_TENANT`
  - `ACTIVITI_DATASOURCE_URL`
  - `ACTIVITI_DATASOURCE_DRIVER`
  - `ACTIVITI_DATASOURCE_USERNAME`
  - `ACTIVITI_DATASOURCE_PASSWORD`
  - `ACTIVITI_HIBERNATE_DIALECT`
  - `ACTIVITI_ADMIN_EMAIL`
  - `ACTIVITI_ADMIN_PASSWORD_HASH`
  - `ACTIVITI_CORS_ENABLED`
  - `ACTIVITI_CORS_ALLOWED_ORIGINS`
  - `ACTIVITI_CORS_ALLOWED_METHODS`
  - `ACTIVITI_CORS_ALLOWED_HEADERS`
  - `ACTIVITI_CSRF_DISABLED`
  - `ACTIVITI_ES_SERVER_TYPE`
  - `ACTIVITI_ES_CLUSTER_NAME`
  - `ACTIVITI_ES_DISCOVERY_TYPE`
  - `ACTIVITI_ES_DISCOVERY_HOSTS`

For better explanation on the role of those environment variables, please consult the PS Documentation

### Importing your own configuration

If you have already a valid Process Services configuration file, you can specify it in the environment variables. To do this, first substitute the exiting variables with:

  - `EXTERNAL_PROPERTIES_FILE`

and then specify the url of the properties file.

**Note**: The url must be visible from the container environment. It will be provisioned to the container at start time.

### Example

```
environment:
  EXTERNAL_PROPERTIES_FILE: https://your-s3-bucket.com/activiti-app.properties
```

## Warning

The examples are provided purely as a means to show you how to orchestrate. We would not advise bringing them directly into a production environment.

You can configure the Process Services image in a scalable, data persistant and high-availability way, however, for the sake of simplicity, the examples cover only the basic configuration.

Initially, you may wish to run Process Services without a containerized database and point it to an external one (self-provided or RDS instance).
