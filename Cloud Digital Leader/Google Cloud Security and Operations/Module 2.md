### Privacy, Security, Compliance, and Availability
* Privacy in the context of cloud technology refers to the data an org or an individual has access to and who they can share that data with.
* Security in the cloud refers to the policies, procedures, and controls put in place to keep data safe.
* Compliance takes data security one step further.
    * It's about meeting standards set by a third party, like a regulatory authority or an international standards organization.
* Availability refers to how much time the cloud service provider guarantees that your data and services are up and running or accessible. 
    * The availability of a service is typically documented as a percent of time per year, for example, 99.999% or 5/9.
        * Services would only be unavailable for five minutes in a year.
* Google Cloud was the first cloud provider to encrypt all customer data by default without customers needing to do anything. 
* ISO 27-0-17 covers the protection of personally identifiable information in cloud services.

### Today's Top Cyber Security Challenges
* Constant criminal attacks: Means that phishing attackers do research to gather info about you or anyone in your org.
    * They then craft highly-targeted emails to trick these people into thinking that the messages are genuine.
* Physical damage: Means that orgs can still be responsible for data losses even when there is damage to the physical hardware, there are power losses, or natural disasters.
* Data can be lost, damaged, or destroyed by viruses or malware.
* A set of files can be rendered unavailable to its intended users via ransomware until the ransom amount is paid. 
* Unsecured third party systems can pose a threat to data security.
* At the rate that tech is changing, investing in the right expertise to assess, develop, implement, and maintain data security plans is essential for businesses to stay ahead of potential data security threats. 

### Shared Responsibility Model - Part I 
* When an org adopts the cloud, the cloud service provider becomes the data processor - the org is the data controller.
* While the cloud service provider manages the security of its infrastructure and its data centers, customers gain the benefits of their infrastructure's multiple built in security laters - referred to as defense in depth.
* The customer's core responsibility is to secure access to data while the cloud provider is responsible for securing the underlying infrastructure.
* As of early 2021, Google Cloud has over 124 points of presence, or POPs, worldwide, connecting 24 data center regions.
    *  Google designs its own server, storage, and networking gear.
    * It (Google) manufactures almost all of its own hardware, and third parties never see the overall process.
    * The hardware is housed in these high security data centers that are located around the world.
* New server builds have an embedded chip called Titan which checks the machine for integrity every time it boots up.
    * The Titan microcontroller continues to verify the operating systems and the rest of the deploy software stack.
    * The server is not allowed onto the network, and it holds zero data until its health is confirmed.
* Storage is closely connected to the idea of encryption at rest.
    * Encryption at rest protects data when it's stored on physical media like a hard disk. 
* All data at rest is also encrypted by default to help guard against unauthorized access.
* When data is going to be stored on Google Cloud, it goes through the following process:
    * First, it's broken into many pieces in memory.
        * These pieces or chunks are encrypted with their own data encryption key or DEK.
        * These DEKs are then encrypted a second time or wrapped, generating another key, a key encryption key or KEK.
        * Encrypted chunks and wrapped encryption keys are distributed across Google's infrastructure. 
    * Next is identity.
        * Google Cloud operates a zero trust model which means that every user and every machine that tries to access data or services must strongly authenticate at every stage for each file. 
   * Anyone accessing the cloud does so via a network.
       * Encryption in transit protects data as it moves across the network.
   * At Google, a global team of more than 900 security experts monitor the system constantly. 

### Shared Responsibility Model - Part II
* IT teams need to have a complete understanding of who can access what data.
    * Need to define who can do what and on what cloud resource.
* Enable multi-factor authentication to protect against phishing.
* Can use security keys to plug in.
* Use logging and monitoring tools, many are natively provided as part of Google Cloud services.
* How do orgs manage a data breach:
    * Need to know what's going on by developing situational awareness.
    * Need to have a culture that allows team to work in stressful situations.
        * Create an open, blameless culture.
    * Need to maintain operational readiness. 

### Identity and Access Management
* Cloud Identity is a Google Cloud solution that helps orgs control and manage access to resources in order to maintain the security and integrity of both data and systems. 
* An identity access management policy or IAM policy is made of three parts: who can do what, and on which resource.
* The who part of an IAM policy can be a Google account, a Google group, a service account, or a Google workspace or Cloud Identity domain.
* The "can do what" part is identified by IAM role.
* Three kinds of Cloud IAM roles: primitive, predefined, and custom.
    * Primitive roles are owner, editor, and viewer and are broad.
        * An account admin, for instance, would apply primitive roles to a Google Cloud project, thereby affecting access to all resources in that project.
        * If you're a viewer of a given resource, you can exame it but not change its state.
        * If you're an editor, you can do everything a viewer can do plus change its state.
        * If you're an owner, you can do everything an editor can do, plus manage roles and permissions on the resource.
        * Assigning primitive roles is not the most effective approach to security.
    * If you're not sure what permissions to grant specific users, Google Cloud services offer their own set of predefined roles that align with typical responsibilities of people using those services.
        * Each role is a collection of permissions.
        * The cloud service defines where those roles can be applied.
        * Compute Engine also provides a set of predefined roles that can be applied to Compute Engine resources in a given project, given folder, or an entire org.
        * Cloud Bigtable, a managed database service, offers roles that can be applied across an entire org, to a particular project, or even to individual big table database instances.
    * Google Cloud recommends using a least privileged model in which each person in your org is given the minimal amount of privilege needed to do their job. 
        * For example, maybe you want to define a role to allow some users to stop and start Compute Engine VMs, but not to reconfigure them.
        * Orgs that use custom roles need to manage the permissions that make them up.
        * An org can map job functions within the org to specific groups and each group can then be given specific roles for specific resources.

### Resource Hierarchy
* Another facet to controlling and managing access is tied to the resource hierarchy, or in other words, what resources users can access.
* A project is the basis for enabling and using Google Cloud capabilities, like managing APIs, enabling billing, adding and removing collaborators, and enabling other Google or Alphabet services.
* A resource is any Google Cloud service, like Compute Engine and BigQuery.
    * Any resources consumed by your project, for example, VMs, Cloud Storage buckets, or BigQuery tables are connected to the project in the hierarchy.
* Businesses usually have more than one cloud project running, so projects can be organized into folders. 
    * A folder can contain projects, other folders, or a combination of both.
* Projects can be grouped into a hierarchy
    * Belong to the organization rather than the user who created them.
    * Used for grouping Google Cloud resources.
    * Can exist under a folder, so it can be grouped logically to match a company's actual structure. 
* Refers to the way the IT team can organize a business's Google Cloud environment, and how that service structure maps to the org's actual structure.
* IT teams can manage access and permissions for groups of related resources.
* Starting from the top, everything in Google Cloud is under a domain and an organization.
    * The domain is handled through Cloud Identity, and helps manage user profiles.
    * The org is managed through the Cloud Console, and lets admins see and control Google Cloud resources and permissions.
    


   
           
         