# Process Services Kubernetes Library
================================

As well as the Docker container source files, we provide 3  worked examples that demonstrate the use of kubernetes in a more practical environment.

  - [Process Services only](./ps-only/ps-only.yml)
  - [Process Services + Postgres](./ps-postgres/ps-postgres.yml)
  - [Process Services + Postgres + ElasticSearch](./ps-postgres-es/ps-postgres-es.yml)

================================

## Instructions:

Create the ps-postgres stack pod

    kubectl create -f ./ps-postgres/ps-postgres.yml

Expose ps-postgres pod

    kubectl expose deployment ps-postgres  --name=process-services --type=LoadBalancer

Check the url and port to access the Process Services

    kubectl describe service process-services

Open browser at http://${IP}:${NodePort}/activiti-app and you will see the application

================================

## Using Minikube

If using [minukube](https://github.com/kubernetes/minikube), you will need to do the following before doing the example:

    minikube start

Create the ps-postgres stack pod:

    kubectl create -f ./ps-postgres/ps-postgres.yml

Expose ps-postgres pod:

    kubectl expose deployment ps-postgres  --name=process-services --type=LoadBalancer

Retrieve the url and port from minikube:

    minikube service process-services --url

Open browser on the indicated url, adding `/activiti-app` at the end of the address
