# Cloud Deployment Manager

### Definitions
* Templated infrastructure deployment.
* An infrastructure deployment service that automates the creation and management of Google Cloud resources.
* A configuration describes all the resources you want for a single deployment. 
    * A configuration file is written in YAML syntax that lists each of the resources you want to create and its respective resource properties.
* A configuration can contain templates, which are essentially parts of the config file that has been abstracted into individual building blocks.
* A resource represents a single API resource.
    * This can be an API resource provided by a Google-managed base type or an API resource provided by a Type Provider.
    * Ex: A Compute Engine instance is a single resource.