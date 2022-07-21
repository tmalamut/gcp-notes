# Logging and Monitoring in the Cloud

### The Importance of Monitoring
* Monitoring is the foundation of product reliability
* It reveals what needs urgent attention and shows trends and application usage patterns which can yield better capacity planning and generally help improve an application clients experience and lessen their pain
* Monitoring is defined as collecting, processing, aggregating, and displaying rela time quantitative data about a system such as query counts and types, error counts and types processing times and server lifetimes
* Can ensure continued system operations, uncover trend analysis over time, build dashboards, alert personnel when systems violate predefined service level objects, compare systems and system changes and provide data for improved incidence response

### Measuring Performance and Reliability
* 4 golden signals that measures a system's performance and reliability: latency, traffic, saturation, and errors
* Latency measures how long it takes a particular part of a system to return a result
* Sample latency metrics include page load latency, number of requests waiting for a thread, query duration, service response time, transaction duration, time to first response, and time to complete data return
* Traffic measurs how many requests are reaching your system
* Sample traffic metrics include the number of HTTP requests per second, number of requests for static versus dynamic content, network IO, number of concurrent sessions, number of transactions per sec, number of retrievals per sec, number of active requests, number of write operations, number of read ops, and number of active connections
* Saturation measures how close to capacity a system is
* Sample capacity metrics include the percent memory utilization, percent thread pool utilization, percent cache utilization, percent disk util, percent CPU util, disk quota, memory quota, number of available connections, and number of users
* Errors are events that measure system failures or other issues
* Sample error metrics include wrong answers or incorrect content, 400 or 500 HTTP codes, number of failed requests, number of exceptions, number of stack traces, servers that fail liveness checks, and number of dropped connections

### SLIs, SLOs, and SLAs
* Need to adjust their expectations for service availability from 100% to a lower percentage.
* In order to roll out updates, operators have to take a system offline.
* Ensuring 100% availability is also incredibly expensive for any business.
* At some point, the marginal cost of reliability exceeds the marginal value of reliability.
* Cloud providers use standard practices to define and measure service availability for customers.
    * A service level agreement (SLA) is a contractual commitment between the cloud service provider and the customer. Provides the baseline level for the quality, availability, and reliability of that service.
    * A service level objective (SLO) is a key element within the SLA - it's the goal for the cloud service performance level, and it's shared between the cloud provider and a customer if the service performance meets or exceeds the SLO.
    * A service level indicator (SLI) is a measure of the service provided. Often includes reliability and errors.
    * An error budget is the amount of error that a service provider can accumulate over a certain period of time before end users start feeling unhappy. Typically the space between the SLA and SLO.

### Integrated Observability Tools
* Observability starts with signals which are metric, logging, and trace data captured and integrated into Google products from the hardware layer up from those products
* The signal data flows into Google Cloud's operations tools where it can be visualized in dashboards and through the metrics
* Explorer automated and custom logs can be dissected and analyzed in the logs
* Explorer services can be monitored for compliance with service level objectives and error budgets can be tracked
* Health checks can be used to check up time and latency for external facing sites and services and running apps can be debugged and profiled
* When incidents occur, signal data can generate automated alerts to code or through various info channels to key personnel

### Monitoring Tools
* Google Cloud, by default, collects more than 1k streams of metric data, which can be incorporated into dashboards, alerts, and several other key tools
* Cloud Monitoring provides visibility into performance, uptime, and overall health of cloud-powered apps
* It collects metrics, events, and metadata from projects, logs, services, systems, agents, custom code, and various app components, including Cassandra, Nginx, Apache Web Server, and Elasticsearch
* Cloud monitoring ingests the data and generates insights via dashboards, metrics explorer charts, and automated alerts

### Logging Tools
* Cloud Logging allows users to collect, store, search, analyze, monitor, and alert on log entries and events
* Automated logging is integrated into products like App Engine, Cloud Run, Compute Engine VMs running the logging agent, and GKE
* Most log analysis starts with Google Cloud's integrated Logs Explorer
* Pub/Sub messages can be analyzed in near real-time using custom code or stream processing technologies like Dataflow
* BigQuery allows analysts to examine logging data thru SQL queries and archive log files in Cloud Storage
* Log data can be exported as files to Cloud Storage, as messages through Pub/Sub, or into BigQuery tables
* Log base metrics can be created and integrated into cloud monitoring dashboards, alerts, in-service SLOs
* Data access logs are retained by default for 30 days, but configurable up to a max of 3650 days. Admin logs are stored by default for 400 days
* 4 key log categories are audit, agent, network, and service
* Cloud audit logs helps answer the question, who did what, where, and when
* Admin activity tracks config changes
* Agent logs use a Google customized and packaged Fluentd agent that can be installed on any AWS or Google Cloud VM to ingest logged data from Google Cloud instances
* Network logs provide both network and security ops with in-depth network security telemetry
* VPC flow logs records samples of VPC network flow, and can be used for network monitoring, forensics, real-time security analysis, and expense optimization
* Service logs provide access to logs created by developers deploying code to Google Cloud

### Error Reporting and Debugging Tools
* Error reporting counts, analyzes, and aggregates the crashes in your running cloud services
* Crashes are exceptions which aren't caught and handled by the code itself
* Its management interface displays the results with sorting and filtering capabilities
* A dedicated view shows the error details, time chart occurrences, affected user count, first and last-seen dates, and a claned exception stack track
* Can also create alerts to receive notifications on new errors
* Cloud Debugger lets you debug your apps while running in production without stopping them or slowing them down
* Can collab with other team members by sharing your debug sessions by sending the console url
* State of app in prod can be captured at a specific line location with snapshots
* Log points can be used to inject a new logging statement on-demand at a specific line location
* Debugger can integrate w/other services/workflows
* Cloud Trace is a tracing system that collects latency data from your distributed apps and displays it in the console
* Can capture traces from apps deployed on App Engine, Compute Engine VMs, and Kubernetes Engine containers
* Trace automatically analyzes all of your apps traces to generate in-depth latency reports to surface performance degradations
* Cloud Profiler helps by using statistical techniques and extremely low impact instrumentation that runs across all production app instances to provide a complete CPU and heap picture of an app without slowing it down
* Help understand which paths consume the most resources and the different ways in which their code is actually called