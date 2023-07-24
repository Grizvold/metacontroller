# Metacontroller Assignment

This repository contains Kubernetes configurations for the Redis CRUD service and Slack notifier service to be run with Metacontroller.

## Prerequisites

You need to have the following installed on your machine:

- Docker Desktop
- kubectl
- kind (Kubernetes in Docker)

## Files

- `crds.yaml`: Contains the CustomResourceDefinitions for the RedisCrud and SlackNotificator.
- `rediscrudservice.yaml`: The instance of the RedisCrud custom resource.
- `slacknotificator.yaml`: The instance of the SlackNotificator custom resource.
- `composite-controllers.yaml`: Contains the CompositeController definitions for RedisCrud and SlackNotificator.
- `rediscrudservice-controller.yaml`: Kubernetes Deployment and Service for the Redis CRUD service.
- `slacknotifier-controller.yaml`: Kubernetes Deployment and Service for the Slack notifier service.

## How to Run

1. Apply the CustomResourceDefinitions:
````
kubectl apply -f crds.yaml
````
2. Apply the RedisCrud and SlackNotificator instances:
````
kubectl apply -f rediscrudservice.yaml
kubectl apply -f slacknotificator.yaml
````

3. Apply the CompositeControllers:

````
kubectl apply -f composite-controllers.yaml
````

4. Deploy the Redis CRUD and Slack notifier services:

````
kubectl apply -f rediscrudservice-controller.yaml
kubectl apply -f slacknotifier-controller.yaml
````


After completing the steps above, you should have the Redis CRUD service and the Slack notifier service running on your Kubernetes cluster, with the custom resources managed by the Metacontroller.

The Redis CRUD service is a RESTful API that allows you to perform CRUD operations on a Redis database.

The Slack notifier service listens for changes in the status of the RedisCrud resource instances and sends notifications to a configured Slack channel.
