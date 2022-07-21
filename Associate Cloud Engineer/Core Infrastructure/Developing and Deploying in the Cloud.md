# Developing and Deploying in the Cloud

### Development in the Cloud
* Many Google Cloud customers use Git repos to store, version, and manage their source code trees
* Means that they either run their own Git instances or they use a hosted Git provider
* But what if there was a third option where you could keep code private to a Google Cloud project and use IAM permissions to protect it but not have to maintain the Git instance - this is called Cloud Source Repositories
* Cloud Source Repos provide full featured Git repos hosted on Google Cloud that support the collaborative dev of any app, including those that run on App Engine and Compute Engine. Can have any number of private Git repos
* Also allows Google Cloud diagnostics tools like debugger and error reporting to use the code, track down issues w/o slowing down users
* Cloud Functions is a lightweight event-based asynchronous compute solution that allows you to create small, single-purpose functions that respond to cloud events w/o the need to manage a server or runtime environment

### Deployment: Infrastructure as Code
* Creating an env in Google Cloud can means lots of work like setting up a compute network and storage resources and then keeping track of their configurations
* If you want to change the env or manually write new commands if you want to clone an env, it's more efficient to use a template
* A template allows you to write the specification to your app env in the same way you'd write a config file
* Can be done with Terraform
* To use Terraform, create a template file using HashiCorp Configuration Language (HCL) that describes what you want the components of the env to look like
* Terraform then uses that template to determine the actions needed to create the env your template describes