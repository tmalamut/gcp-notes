# Cloud IAM

### Definitions
* Resource access control
* Lets you create and manage permissions for GCP resources.
* Unifies access control for GCP services into a single system and presents a consistent set of operations.
* Manage access control by defining who (identity) has what access (role) for which resource.
* The organizations, folders, and projects that you use to organize your resources are also resources.
* Permission to access a resource isn't granted directly to the end user. Instead, permissions are grouped into roles, and roles are granted to authenticated principals.
* An allow policy (IAM policy) defines and enforces what roles are granted to which principals. When an authenticated principals attempts to access a resource, IAM checks the resource's allow policy to determine whether the action is permitted.
* Model for access management has three main parts:
    * Principal: Can be a Google account (for end users), a service account (for apps and compute workloads), a Google group, or a Google Workspace account or Cloud Identity domain that can access a resource.
    * Role: A role is a collection of permissions. Permissions determine what operations are allowed on a resource. When you grant a role to a principal, you grant all the permissions that the role contains.
    * Policy: The allow policy is a collection of role bindings that bind one or more principals to individual roles. When you want to define who (principal) has what type of access (role) on a resource, you create an allow policy and attach it to the resource.