# Identity and Access Management (IAM)

### IAM
* It is a way of identifying who can do what on which resource
* The who can be a person, group, or app
* The what refers to specific privileges or actions and the resource could be of any Google Cloud service
* The organization node is the root node in hierarchy, followed by folders, projects, then resources

### Organization
* An organization node is a root node for Google Cloud resources
* Organization roles:
    * Organization Admin: Control over all cloud resources; useful for auditing
    * Project Creator: Controls project creation; control over who can create projects
* Created when a Google Workspace or Cloud Identity account creates a Google Cloud project
* Workspace or Cloud Identity super admin:
    * Assign the Organization admin role to some users
    * Be the point of contact in case of recovery issues
    * Control the lifecycle of the Workspace or Cloud Identity acount and Organization resource
* Organization admin:
    * Define IAM policies
    * Determine the structure of the resource hierarchy
    * Delegate responsibility over critical components such as Networking, Billing, and Resource Hierarchy through IAM roles
* Folders
    * Additional grouping mechanism and isolation boundaries between projects:
        * Different legal entities
        * Departments
        * Teams
    * Folders allow delegation of admin rights
* Resource manager roles:
    * Organization:
        * Admin: Full control over all resources
        * Viewer: View access to all resources
    * Folder:
        * Admin: Full control over folders
        * Creator: Browse hierarchy and create folders
        * Viewer: View folders and projects below a resource
    * Project:
        * Creator: Create new projects (automatic owner) and migrate new projects into organization
        * Deleter: Delete projects

### Roles
* IAM basic roles apply across all Google Cloud services in a project
* Basic roles offer fixed, coarse-grained levels of access
    * Owner:
        * Invite members
        * Remove members
        * Delete projects
        * And anything editor can do
    * Editor:
        * Deploy apps
        * Modify code
        * Configure services
    * Viewer
        * Read-only access
    * Billing Administrator
        * Manage billing
        * Add and remove admins
* IAM predefined roles apply to a particular GCP service in a project
* Predefined roles offer more fine-grained permissions on particular services
* Predefined roles are a collection of permissions
* Compute Engine has several predefined roles, like:
    * Compute Admin:
        * Full control of all Compute Engine resources
    * Network Admin:
        * Permissions to create, modify, and delete networking resources, except for firewall rules and SSL certificates
    * Storage Admin:
        * Permissions to create, modify, and delete disks, images, and snapshots
* IAM custom roles let you define a precise set of permissions
* A lot of companies use the least privileged model in which each person in your organization is given the minimal amount of privilege needed to do their job
* If you want to define an instance operator role to allow some users to start and stop Compute Engine VMs but not reconfigure them, custom roles allow you to do that

### Members
* 5 different types of members: Google accounts, Service accounts, Google groups, Google Workspace domains, and Cloud Identity domains
* A Google account represents a developer, admin, or any other person who interacts with Google Cloud. Any email address that is associated with a Google account can be an identity including Gmail.com or other domains
* A service account is an account that belongs to your app instead of an individual end user. When you run code that is hosted in Google Cloud, you specify an account that that code should run as. You can create as many service accounts as needed to represent the different logical components of your app
* A Google group is a named collection of Google accounts and service accounts. Every group has a unique email address that is associated with that group. Are a convenient way to apply an access policy to a collection of users
* A Workspace domain represents a virtual group of all the Google accounts that have been created in an org's workspace account. Represent your org's internet domain name
* Cloud Identity lets you manage users and groups using Google Admin console, but you don't pay for or receive Workspace's collaboration products such as Gmail, Docs, Drive
* Cannot use IAM to create or manage your users or groups. Instead, you can use Cloud Identity or Workspace to manage users
* IAM policies:
    * A policy consists of a list of bindings
    * A binding binds a list of members to a role
* IAM conditions:
    * Enforce conditional, attribute-based access control for Google Cloud resources
        * Grant resource access to identities (members) only if configured conditions are met
        * Specified in the role bindings of a resource's IAM policy
* An organization policy is:
    * A configuration of restrictions
    * Defined by configuring a constraint with desired restrictions
    * Applied to the org node, folders, or projects
* What if you already have a different corporate directory?
    * Using Google Cloud Directory Sync, your admins can login and manage Google Cloud resources using the same username and passwords that they already use
    * This tool syncs users and groups from your existing active directory or LDAP system with users and groups in your Cloud Identity domain

### Service Accounts
* Service accounts provide an identity for carrying out server-to-server interactions
    * Programs running within Compute Engine instances can automatically acquire access tokens with credentials
    * Tokens are used to access any service API in your project and any other services that granted access to that service account
    * Service accounts are convenient when you're not accessing user data
* Are identified by an email address
    * Three types of service accounts:
        * User-created (custom)
        * Built-in
            * Compute Engine and App Engine default service accounts
        * Google APIs service account
            * Runs internal Google processes on your behalf
* Default Compute Engine service account
    * Automatically created per project with auto-generated name and email address
    * Automatically added as a project editor
    * By default, enabled on all instances created using gcloud or Cloud Console
* Scopes are used to determine whether an authenticated identity is authorization
    * Ex: App A getting read-only scope on a bucket while App B gets read-write
    * Scopes can be changed after the instance is created by stopping it
* Service account permissions
    * Default service accounts: basic and predefined roles
    * User-created service accounts: predefined roles
    * Roles for service accounts can be assigned to groups or users
    * Can be changed without re-created VMs
* Two types of Google Service Accounts:
    * Google-managed service accounts
        * All service accounts have Google-managed keys
        * Google stores both the public and private portion of the key
        * Each public key can be used for signing for a max of two weeks
        * Private keys are never directly accessible
    * User-managed service accounts
        * Google only stores the public portion of a user-managed key
        * Users are responsible for private key security
        * Can create up to 10 user-managed service account keys per service
        * Can be administered via the IAM API, gcloud, or the Console

### IAM Best Practices
* Leverage and understand the resource hierarchy
    * Use projects to group resources that share the same trust boundary
    * Check the policy granted on each resource and make sure you understand the inheritance
    * Use "principles of least privilege" when granting roles
    * Audit policies in Cloud Audit Logs: setiampolicy
    * Audit membership of groups used in policies
* Grant roles to Google groups instead of individuals
    * Update group membership instead of changing IAM policy
    * Audit membership of groups used in policies
    * Control the ownership of the Google group used in IAM policies
* Service accounts
    * Be very careful granting serviceAccountUser role
    * When you create a service account, give it a display name that clearly identifies its purpose
    * Establish a naming convention for service accounts
    * Establish key rotation policies and methods
    * Audit with serviceAccount.keys.list() method
* Identity-Aware Proxy (IAP)
    * Enforce access control polices for apps and resources
        * Identity-based access control
        * Central authorization layer for apps accessed by HTTPS
    * IAM policy is applied after authentication

    








