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
* 






