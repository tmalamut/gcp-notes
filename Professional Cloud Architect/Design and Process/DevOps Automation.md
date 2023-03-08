# DevOps Automation

### Continuous Integration Pipelines
* Continuous integration pipelines automate building applications
* Developers check-in code
    * Use a Git repo for each microservice and branches for versions
* Run unit tests
    * If the tests don't pass, stop
* Build deployment package
    * Create a Docker image
* Deploy
    * Save your new Docker image in a container registry
* Google provides the components required for a continuous integration pipeline
* Cloud Source Repositories
    * Developers push to a central repo when they want a build to occur
    * Provides managed Git repos
    * Control access to your repos using IAM within your Google Cloud project
* Cloud Build
    * Build system executes the steps required to make a deployment package or Docker image
    * Google-hosted Docker build service
        * Alternative to using Docker build command
    * Use the CLI to submit a build
        * gcloud builds submit --tag gcr.io/your-project-id/image-name
* Container Registry 
    * Store your Docker images or deployment packages in a central location for deployment
    * Images built using Cloud Build are automatically saved in Container Registry
    * Can use Docker push and pull commands
    * Binary authorization allows you to enforce deploying only trusted containers into GKE
        * Enable binary authorization on GKE cluster
        * Add a policy that required signed images
        * When an image is built by Cloud Build an "attestor" verifies that it was from a trusted repo
        * Container Registry includes a vulnerability scanner
* Build triggers
    * Watches for changes in the Git repo and starts the build
    * Watch a repo and build a container whenever code is pushed

### Infrastructure as Code
* IaC allows quick provisioning and removing of infrastructure
* Build an infrastructure as needed
* Destroy the infrastructure when not in use
* Create identical infrastructures for dev, test, and prod
* Can be part of a CI/CD pipeline
* Templates are the building blocks for disaster recovery procedures
* Manage resource dependencies and complexity
* Google Cloud supports many IaC tools
* Terraform is an infrastructure automation tool
    * Repeatable deployment process
    * Declarative language
    * Focus on the app
    * Parallel deployment
    * Template-driven