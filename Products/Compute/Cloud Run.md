# Cloud Run

### Definitions
* A fully managed serverless platform that runs individual containers.
* You give code or a container to Cloud Run, and it hosts and auto scales as needed to respond to web and other events.
* Opposite to GKE: Don't have to worry about scaling the infrastructure - just have to write your application code, package it into a container, and deploy it.

### When To Use
* When you need:
    * Fully-managed infrastructure
    * Rapid autoscaling from, and to 0 HTTP/Websockets/gRPC/Events
    * No fixed infrastructure footprint
* Just need to deploy a containerized app in a programming language of your choice with HTTP/s and websocket support.
* Ex: websites, APIs, data processing apps, webhooks.

