# Process Services Kubernetes Library
================================

As well as the Docker container source files, we provide 3  worked examples that demonstrate the use of kubernetes in a more practical environment.

  - [Process Services only](./ps-only/ps-only.yml)
  - [Process Services + Postgres](./ps-postgres/ps-postgres.yml)
  - [Process Services + Postgres + ElasticSearch](./ps-postgres-es/ps-postgres-es.yml)

================================

# Instructions: (for example for Process Services + Postgres (ps-postgres))

## Create the ps-postgres stack pod

$kubectl create -f ./ps-postgres.yml

## Exposing ps-postgres pod

$kubectl expose pod ps-postgres --port=8080 --name=activiti --type=NodePort

## Check the url and port to access the Process Services

$kubectl describe pod ps-postgres

## do not forget the /activiti-app after the port!

================================

# minikube

If using minukube, you will need to do before doing the example,

$minikube start

after starting, do the same thing as in the example, but in the end to check the url and the port you can use:

$minikube service activiti-es --url
