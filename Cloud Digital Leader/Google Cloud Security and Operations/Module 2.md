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
* 
           
         