# Resource Monitoring

### Monitoring
* Monitoring is important to Google because it's at the base of site reliability engineering (SRE)
* SRE is a discipline that applies aspects of software engineering to operations whose goals are to create ultra-scalable and highly reliable software systems
* Cloud Monitoring dynamically configures monitoring after resources are deployed and has intelligent defaults that allow you to easily create charts for basic monitoring activities
* Allows you to monitor your platform, system, and app metrics by ingesting data, such as metrics, events, and metadata
* A metrics scope is the root entity that holds monitoring and config info in Cloud Monitoring
* Each metrics scope can have between 1 and 100 monitoring projects
* Can have as many metrics scopes as you want, but Google Cloud projects and AWS accounts can't be monitored by more than one metrics scope
* A metrics scope contains the custom dashboards, alerting policies, uptime checks, notification channels, and group definitations that you use with your monitored projects
* Can create alerting policies, for example, when the network egress of your VM instances goes above a certain threshold for a specific timeframe
* Recommend alerting on symptoms and not necessarily causes, for example, want to monitor failing queries and then identify whether the database is down
* Monitoring Agent is supported for Compute Engine and EC2 instances and gives additional access to system resource and app service metrics

### Logging
* Platform, systems, and app logs
    * API to write to logs
    * 30-day retention
* Log search/view/filter
* Log-based metrics
* Monitoring alerts can be set on log events
* Data can be exported to Cloud Storage, BigQuery, Pub/Sub

### Error Reporting
* Aggregate and display errors for running cloud services
    * Error notifications
    * Error dashboard
    * App Engine, Apps Script, Compute Engine, Cloud Functions, Cloud Run, GKE, Amazon EC2
    * Go, Java, .NET, Node.js, PHP, Python, Ruby

### Tracing
* Tracing system
    * Displays data in near real-time
    * Latency reporting
    * Per-URL latency sampling
* Collects latency data
    * App Engine Google HTTP(S) load balancers
    * Apps instrumented with the Cloud Trace SDKs

### Debugging
* Inspect an app without stopping it or slowing it down significantly
* Debug snapshots
    * Capture call stack and local variables of a running app
* Debug logpoints
    * Inject logging into a service without stopping it
* Java, Python, Go, Node.js, Ruby, PHP, .NET Core


