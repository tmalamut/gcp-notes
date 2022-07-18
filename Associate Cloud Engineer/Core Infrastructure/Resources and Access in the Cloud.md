# Resources and Access in the Cloud

### Google Cloud Resource Hierarchy
* Four levels (top to bottom):
    * Organization node
    * Folder
    * Project
    * Resources
* Resources represent things like VMs and Cloud Storage buckets
* Resources are organized into projects
* Projects are organized into folders or subfolders
* The resource hierarchy directly relates to how policies are managed and applied on Google Cloud
* Policies can be defined at the project, folder, and organization level
* Some Google Cloud services allow policies to be applied to individual resources
* Policies are inherited downward - if a policy is applied to a folder, it will be apply to all of its projects
* Projects are the basis of enabling and using services, like managing APIs, enabling billing
    * Hold resources, each of which belong to just one project
    * Can have different owners and users
    * Are billed and managed separately
    * Have 3 identifying attributes
        * Project ID
            * Globally unique
            * Assigned by Google Cloud but mutable during creation
            * Immutable after creation
        * Project name
            * Need not be unique
            * Chosen by you
            * Mutable
        * Project number
            * Globally unique
            * Assigned by Google Cloud
            * Immutable
* Resource Manager Tool is designed to programmatically help you manage projects. An API that can:
    * Gather a list of projects
    * Create new projects
    * Update existing projects
    * Delete projects
    * Recover previously deleted projects
    * Access through RPC API and REST API
* Folders let you assign policies to resources at a level of granularity that you choose
    * The resources in a folder inherit policies and permisions assigned to that folder
    * Can contain projects, other folders, or a combo of both
    * Can use folders to group projects under an org in a hierarchy
    * For example, your org might contain multiple depts, each with its own set of resources
    * Allow you to group these resources on a per dept basis
    * Give teams the ability to delegate admin rights, so that they can work independently
* Organization node is the very topmost resource in the hierarchy
    * Can designate an org policy admin, so that only people with the right privileges can change policies
    * Can assign a project creator rule
    * Google Workspace customers will have projects automatically belong to the org node
    * Otherwise, use Cloud Identity to create org node

### Identity and Access Management (IAM)
* Admins can apply policies that define who can do what on which resources
* The Who can be a Google account, a Google group, a service account, or a Cloud Identity domain
* The Can-do what part is defined by a role
* An IAM role is a collection of permissions
* For example, to manage VM instances in a project, you must be able to create, delete, start, stop, and change VMs, so these permissions are grouped into a role to make them easier to understand and easier to manage
* When a user, group, or service account is given a role on a specific element of the resource hierarchy, the resulting policy applies to both the chosen element and all the elements below it in the hierarchy.
* Three kinds of roles: Basic, Predefined, Custom
    * Basic roles are quite broad in scope. When applied to a project, they affect all resources in that project. Include Owner, Eidtor, Viewer, and Billing Admin
    * Specific Google Cloud services offer sets of predefined roles and they even define where those roles can be applied
        * For Example, can apply specific predefined roles such as Instance Admin to Compute Engine resources in a given project, folder, or entire org
    * Custom role used if need more specific permissions
        * Many companies use a least privileged model in whcih each person is given the minimal amount of privilege needed to do their job
        * For example, might want to define an Instance Operator role to some users to stop and start Compute Engine VMs but not reconfigure them - custom roles will allow you to define those exact permissions
        * Custom roles can't be applied to the folder level - only project and org
        * Custom roles must be managed so some companies decide they're rather use the predefined roles

### Service Accounts
* What if you want to give permissions to a Compute Engine VM rather than to a person?
* Example: Have an app running in a VM that needs to store data in Cloud Storage, but you don't want anyone on the internet to have access to that data - just that particular VM. You can create a service account to authenticate that VM to Cloud Storage
* Service accounts are named with an email address, but instead of passwords, they use cryptographic keys to access resources
* Do need to be managed
* Is also a resource so it can policies of its own attached to it

### Cloud Identity
* Orgs can define policies and manage their users and groups using the Google Admin Console
* Admins can log in and manage resources using the same usernames and passwords they already used in existing Active Directory or LDAP systems
* When someone leaves an org, an admin can use the Google Admin Console to disable their account and remove them from groups
* Is available in a free edition and also in a premium edition that provides capabilities to manage mobile devices
* If you're a Google Cloud customer who is also a Google Workspace customer, this functionality is already available 

### Interacting with Google Cloud
* 4 ways to interact: Cloud Console, Cloud SDK and Cloud Shell, APIs, and Cloud Console Mobile App
* Cloud Console:
    * Simple web-based graphical user interface
    * Easily find resources, check their health, have full management control over them, and set budgets
    * Provides a search facility to quickly find resources and connect to instances via SSH in the browser
* Cloud SDK and Cloud Shell:
    * Set of tools to manage resources and apps hosted on Google Cloud:
        * gcloud tool: Provides the main command-line interface for Google Cloud products & services
        * gsutil: Provides access to Cloud Storage from the command line
        * bq: A command-line tool for BigQuery
    * Cloud Shell is a Debian-based VM with a persistent 5GB home directory, which makes it easy to manage projects and resources
* APIs:
    * Google Cloud services offer APIs that allow code to be written to control them
    * The Google APIs Explorer shows what APIs are available, and in what versions
    * Google provides Cloud Client and Google API Client libraries
    * Languages currently represented: Java, Python, PHP, C#, Go, Node.js, Ruby, and C++
* Cloud Console Mobile App:
    * Start, stop, and use SSH to connect into Compute Engine instances, and see logs
    * Stop and start Cloud SQL instances
    * Administer apps deployed on App Engine
    * Up-to-date billing info for projects and alerts for those going over budget
    * Customizable graphs showing key metrics
 
