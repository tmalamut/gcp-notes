### IT Development and Operations Challenges
* For orgs to thrive in the cloud, need to adapt their IT operations.
* Need to adjust their expectations for service availability from 100% to a lower percentage.
    * In order to roll out updates, operators have to take a system offline.
    * Ensuring 100% availability is also incredibly expensive for any business. 
    * At some point, the marginal cost of reliability exceeds the marginal value of reliability.
    * Cloud providers use standard practices to define and measure service availability for customers.
        * A service level agreement (SLA) is a contractual commitment between the cloud service provider and the customer. Provides the baseline level for the quality, availability, and reliability of that service. 
        * A service level objective (SLO) is a key element within the SLA - it's the goal for the cloud service performance level, and it's shared between the cloud provider and a customer if the servide performance meets or exceeds the SLO. 
        * A service level indicator (SLI) is a measure of the service provided. Often includes reliability and errors. 
        * An error budget is the amount of error that a service provider can accumulate over a certain period of time before end users start feeling unhappy. Typically the space between the SLA and SLO. 
* Need to adopt best practices from the developer operations or DevOps, and site reliability engineering or SRE so teams can be more agile and work more collaboratively with clearer accountability.

### DevOps and SRE
* Developer operations (DevOps) is a philosophy that seeks to create a more collaborative and accountable culture within developer and operations teams.
* Google's five objectives of DevOps:
    * It allows orgs to reduce silos - can increase and foster collaboration by breaking down barriers across teams.
    * Orgs need to accept failure as normal.
    * Orgs need to implement gradual change - small incremental changes are easier to review. 
    * Businesses should leverage tooling and automation - identifying manual work that can be automated is key to working efficiently and focusing on the tasks that matter.
    * Orgs need to measure everything - measurement is a critical gauge for success.
* Site reliability engineering (SRE) is a discipline that applies affects of software engineering to operations.
    * Goals of SRE are to create ultra-scalable and highly reliable software systems.
* SRE best practices:
    * Emphasizes shared ownership of production between developers and operations. Together, they define SLOs, calculate error budgets, and determine reliability and order work priorities.
    * SREs believe that accepting failure as normal helps to build an iterative collaborative culture. 
    * When implementing gradual changes, SREs aim to reduce the cost of failure by rolling out changes to a small percentage of users before making them generally available. 
    * SREs focus on toil (work tied to running a production service) automation - reduces the amount of manual repetitive work.
    * Measure everything means tracking everything related to toil, reliability, and the health of their systems. 

### Google Cloud Resource Monitoring Tools
* Google Cloud's operations suite offer a range of services and cloud computing resources to monitor, troubleshoot, and improve app performance on an org's Google Cloud environment.
* Tools included in Google Cloud's operation suite fall into two major categories: 
    * Operations focus tools, which include cloud monitoring, cloud logging, error reporting, and service monitoring.
    * Application performance management tools, which includes Cloud Debugger, Cloud Trace, and Cloud Profiler.
* The term monitoring refers to gathering predefined sets of metrics or logs.
    * Cloud monitoring is the foundation for SRE because it provides visibility into the performance, uptime, and overall health of cloud powered apps.
    * Businesses can collect metrics, events, and metadata from Google Cloud services, visualize them on charts and dashboards, and manage alerts.
    * Also evaluates the performance of the entire infrastructure on a modular level.
    * Means that properties such as server uptime, and response rate can help in evaluating customer experience.
* Cloud Logging is another resource monitoring tool.
    * A log file is a text file where apps including the OS write events.
    * Log files make it easier for devs, DevOps, and system admins to get insights and identify the root cause ofi ssues within apps and the infrastructure.
    * Google Cloud Logging is a fully managed service that performs at scale and can ingest app and system log data as well as custom log data from Google Kubernetes Engine (GKE) environments, VMs, and Google Cloud services.
    * Allows IT teams to analyze selected logs and accelerate app troubleshooting.
* Cloud Debugger helps monitor app performance.
    * IT teams can inspect the state of running apps in real time without stopping or slowing it down.
    * Can use it to understand the behavior of code in production.
* Cloud Trace is another Google Cloud solution for monitoring app performance.
    * When an app architecture is chunked into small pieces using microservices or containers, or both, finding the source of a bug or problem can be challenging.
    * Cloud Trace is a distributed tracing system that helps devs debug or fix and optimize their code.