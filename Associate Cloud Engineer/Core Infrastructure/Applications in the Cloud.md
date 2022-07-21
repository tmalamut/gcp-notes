# Applications in the Cloud

### App Engine
* App Engine is a fully managed, serverless platform for developing and hosting web apps at scale
* Can choose from popular coding languages, libraries, and frameworks to develop apps then automatically provision servers and scale app instances based on demand
* No servers to provision or maintain
* Provides built-in services and APIs like NoSQL data stores, memcache, load balancing, health checks, app logging and a user auth API
* Offers SDKs to help you develop, deploy, and manage app on local machine
* Each SDK includes all of the APIs and libraries available to App Engine, the simulated secure sandbox environment that emulates all of the App Engine services on your local machine and deployment tools to upload your app to the cloud and manage different versions
* SDK manages your app locally, and the Google Cloud Console manages your app in production
* Can use the Cloud Console web-based interface to create new apps, configure domain names, change which version of your app is live, examine access and error logs and much more
* From a security perspective, the Security Command Center, Google Cloud's security and risk management platform, keeps web apps safe
* Thorugh Cloud Console, can use Security Command Center to automatically scan and detect common web app vulnerabilities

### App Engine Environments
* 2 types of App Engine environments: Standard and Flexible
* App Engine standard environment is based on container instances running on Google's infrastructure
* Containers are pre-configured with a runtime from a standardized list of supported languages and versions, which includes libraries that support App Engine standard APIs
* For many apps, standard environment runtime and libraries may be all you need
* Standard enviornment features include persistent storage with queries, sorting and transactions, automatic scaling and load balancing, asynchronous task queues for performing work outside the scope of a request, scheduled tasks for triggering events at specified times or regular intervals, and integration with other Google Cloud servides and APIs
* Couple of requirements for using the standard enviornment - must use specific versions of Java, Python, PHP, Go, Node.js, and Ruby and your app must conform to sandbox constraints that are dependent on runtime
* Standard environment workflow typically follows 3 steps:
    * Web app is developed and tested locally
    * SDK is used to deploy the app to App Engine
    * App Engine scales and services the app
* Flexible environment lets you specify the type of container your web app will run in
* This option lets an app app run inside Docker containers on Google Cloud's Compute Engine VMs - in this case, App Engine manages Compute Engine machines for you. Means that instances are health-checked, healed as necessary, and co-located with other module instances within the project
* VM instances are restarted on a weekly basis
* Flexible env supports microservices, authorization, SQL and NoSQL databases, traffic splitting, logging, search, versioning, security scanning, Memcache, and content delivery networks
* Flexible allows users to also benefit from custom configs and libraries while still keeping their main focus on writing code
* Flexible allows you to customize the runtime in the OS of your VM by using Docker files
* For pricing, you pay per instance class with automatic shutdown in standard
* For flexible, you pay for resource allocation per hour with no automatic shutdown
* Flexible is between standard and GKE

### Google Cloud API Management Tools
* Google Cloud provides two API management tools: Cloud Endpoints and Apigee Edge
* Cloud Endpoints is a distributed API management system that uses a distributed extensible service proxy, which is a service proxy that runs in its own Docker container
* Goal is to help you create and maintain even the most demanding APIs with low latency and high performance
* Cloud Endpoints provides an API console, hosting, logging, monitoring, and other features to help you create, share, maintain, and secure your APIs
* Can use Cloud Endpoints with any APIs that support the open API specification
* Cloud Endpoints supports apps running on App Engine, GKE, and Compute Engine
* Apigee Edge has a specific focus on business problems like rate limiting, quotas, and analyrics
* Many Apigee Edge users provide a software service to other companies
* Backend services for Apigee Edge don't have to be in Google Cloud - as a result, engineers also often use it to take apart legacy apps. Instead of replacing a large app in one move, they can use Apigee Edge to peel off its services individually instead

### Cloud Run
* Cloud Run is a managed compute platform that lets you run stateless containers via web requests or Pub/Sub events
* Is serverless, meaning it removes all infrastructure management tasks so you can focus on developing apps
* Built on Knavite, an open API and runtime env built on Kubernetes that gives you freedom to move your workloads across different envs and platforms
* Automatically scales up and down from zero almost instantaneously
* Charges you only for the resources you use, calculated down to the nearest 100ms
* Cloud Run developer workflow is a 3 step process
    * Write your app. This app should start a server that listens for web requests
    * Build and package your app into a container image
    * Container image is pushed to Artifact Registery where Cloud Run will deploy it
* Cloud Run can only deploy images that are stored in Artifact Registry
* Once you've deployed your container image, you'll get a unique HTTPS URL back
* Can also deploy source code instead of a container image
