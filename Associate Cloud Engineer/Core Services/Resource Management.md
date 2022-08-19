# Resource Management

### Resource Manager
* The resource manager lets you hierarchically manage resources by project, folder, and organization
* IAM policies are inherited from top to bottom, but billing is accumulated from the bottom up
* Resource consumption is measured in quanitites like the rate of use or time, number of items, or feature use
* Each project is associated with one billing account, which means that an org contains all billing accounts
* Resources are categorized as global, regional, or zonal
* Images, snapshots, and networks are global resources
* External IP addresses are regional resources
* Instances and disks are zonal resources
* Regardless of the type, each resource is organized into a project - this enables each project to have its own billing and reporting

### Quotas
* All resources are subject to project quotas or limits
    * How many resources you can create per project
        * Ex: 15 VPC networks/project
    * How quickly you can make API requests in a project: rate limits
        * Ex: 5 admin actions/second (Cloud Spanner)
    * How many resources you can create per region
        * Ex: 24 CPUs region/project
* Increase: Quotas page in Cloud Console or a support ticket
* Why use project quotas?
    * Prevent runaway consumption in case of an error or malicious attack
    * Prevent billing spikes or surprises
    * Forces sizing consideration and periodic review

### Labels
* Labels are a utility for organizing GCP resources
* Attached to resources: VM, disk, snapshot, image
    * GCP console, gcloud, or API
* Example uses of labels:
    * Inventory
    * Filter resources
    * In scripts
        * Help analyze costs
        * Run bulk operations
* Use labels for…
    * Team or Cost Center
    * Components
    * Environment or stage
    * Owner or contact
    * State
* Comparing labels and tags
    * Labels are a way to organize resources across GCP
        * disks, image, snapshots...
    * User-defined strings in key-value format
    * Propagated thru billing
    * Tags are applied to instances only
    * User-defined strings
    * Tags are primarily used for networking (applying firewall rules)

### Billing
* To help with project planning and controlling costs, you set a budget - setting a budget lets you track how your spend is growing towards that amount
* Can set budget alerts
* Can use Cloud Pub/Sub notifications to programmatically receive spend updates about this budget
* Can also create a Cloud Function that listens to the Pub/Sub topic to automate cost management


   