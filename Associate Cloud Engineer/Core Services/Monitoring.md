# Monitoring
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