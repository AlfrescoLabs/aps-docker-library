[![Join the chat at https://gitter.im/Alfresco/aps-docker-library](https://badges.gitter.im/Alfresco/aps-docker-library.svg)](https://gitter.im/Alfresco/aps-docker-library?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

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
   - [README](./kubernetes/README.md)
   - [Process Services only](./kubernetes/ps-only/ps-only.yml)
   - [Process Services + Postgres](./kubernetes/ps-postgres/ps-postgres.yml)
   - [Process Services + Postgres + ElasticSearch](./kubernetes/ps-postgres-es/ps-postgres-es.yml)
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

The examples are provided purely as a means to show you how to orchestrate.
We would not advise bringing them directly into a production environment.

## License and Authors

Author: Alfresco DevOps Team (devops@alfresco.com)

Copyright 2017, Alfresco

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
