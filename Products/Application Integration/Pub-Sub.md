# Pub/Sub

### Definitions
* Global real-time messaging.
* A fully-managed real-time messaging service that allows you to send and receive messages between independent apps.
* Allows services to communicate asynchronously, with latencies on the order of 100 milliseconds. 
* Used for streaming analytics and data integration pipelines to ingest and distribute data.
* Equally effective as a messaging-oriented middleware for service integration or as a queue to parallelize tasks.
* Enables you to create systems of event producers and consumers, called publishers and subscribers.
* Publishers communicate with subscribers asynchronously by broadcasting events, rather than by synchronous remote procedure calls (RPCs).
* Publishers send events to the Pub/Sub service, without regard to how or when these events are to be processed. Pub/Sub then delivers events to all services that need to react ot them. 

### When To Use
* Common use cases:
    * Ingestion user interaction and server events
    * Real-time event distribution
    * Replicating data among databases
    * Parallel processing and workflows
    * Enterprise event bus
    * Data streaming from apps, services, or IoT devices
    * Refreshing distributed caches
    * Load balancing for reliability