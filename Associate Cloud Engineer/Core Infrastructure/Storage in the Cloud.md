# Storage in the Cloud

### Cloud Storage
* Cloud Storage offers durable and highly available object storage
* Object storage is a computer data storage architecture that manages data as objects
* These objects are stored in a packaged format which contains the binary form of the actual data itself as well as relevant associated metadata such as date created, author, resource type and permissions and a globally unique identifier
* These unique keys are in the form of URLs, which means object storage interacts well with web technologies
* Data commonly stored as objects include video, pictures, and audio recordings
* Allows customers to store any amount of data and to retrieve it as often as needed
* It's a fully managed service that has a wide variety of uses
* Ex: Serving website content, storing data for archival and disaster recovery, and distributing large data objects to end users via direct download
* Primary use is whenever binary large object storage, also known as BLOB, is needed for online content such as videos and photos for backup and archive data and for storage of intermediate results in processing workflows
* Cloud Storage files are organized into buckets
* A bucket needs a globally unique identifier and a specific geographic location for where it should be stored and an ideal location for a bucket is where latency is minimized
* Storage objects offered are immutable, which means you don't edit them, but instead a new version is created with every change made
* Admins have the option to either allow each new version to completely overwrite the older one or keep track of each change made in a particular object by enabling versioning within a bucket
* If versioning, Cloud Storage will keep a detailed history of modifications
* If you don't turn on object versioning, by default new versions will always overwrite older versions
* With object versioning enabled, you can list the archive versions of an object, restore an object to an older state or permanently delete a version of an object as needed
* PII might be contained in data objects, so controlling access to stored data is essential to ensuring security and privacy are maintained
* Using IAM roles and where needed, orgs can conform to security best practices which require each user to have access and permissions to only the resources they need to do their job and no more than that
* Couple of options to control user access to objects and buckets - for most purposes, IAM is sufficent. Roles are inherited from project to bucket to object
* If need finer control, can create access control lists. Each access control list consists of 2 pieces of info:
    * First is a scope which defines who can access and perform an action. This can be a specific user or group of users
    * Second is a permission which defines what actions can be performed like read or write
* Offers lifecycle management policies to save money
    * Could tell Cloud Storage to delete objects older than 365 days or to delete objects created before January 1, 2013 or to only keep the 3 most recent versions of each object in a bucket that has versioning enabled

### Cloud Storage: Storage Classes and Data Transfer
* Four primary storage classes in Cloud Storage
* Standard storage is considered best for frequently accessed or hot data. Also great for data that's only stored for only brief periods of time
* Nearline storage is best for storing infrequently accessed data, like reading or modifying data on average once a month or less. Examples might include data backups, long-tail multimedia content, or data archiving
* Coldline storage is a low cost option for storing infrequently accessed data at most once every 90 days
* Archive storage is the lowest cost option used ideally for data archiving, online backup, and disaster recovery. Best choice for data that you plan to access less than once a yr
* All storage classes have unlimited storage with no minimum object size requirement, worldwide accessibility and locations, low latency and high durability
* Always encrypts data on the server-side before it's written to disk at no additional charge
* Data traveling between a customer's device and Google is encrypted by default using HTTP/TLS, which is Transport Layer Security
* Data can be moved using gsutil, which is the Cloud Storage command from the Cloud SDK
* Can also be moved by using drag and drop in Cloud Console on Chrome
* Storage Transfer Service enables you to import large amounts of online data. Lets you schedule and manage batch transfers to Cloud Storage from another cloud provider, different Cloud Storage region, or from an HTTPS endpoint
* Transfer Appliance is a high-capacity storage server that you lease from Google Cloud. You connect ito your network, load it with data, and then ship it to an upload facility where the data is uploaded to Cloud Storage. Can transfer up to a petabyte of data on a single appliance
* Cloud Storage's tight integration with other Google Cloud products and services means that there are many additional ways to move data into the service
* Ex: Can import and export tables to and from BigQuery in Cloud SQL
* Can also store AppEngine logs, Firestore backups and objects used by AppEngine apps like images
* Can also store instance startup script, Compute Engine images and objects used by Compute Engine apps

### Cloud SQL
* Offers fully managed relational databases, including MySQL, PostgreSQL, and SQL server as a service
* Designed to hand off mundane but necessary and often time consuming tasks to Google, like applying patches and updates, managing backups, and configuring replication
* Doesn't require any software installation or maintenance
* Can scale up to 64 processor cores, 400+ GB of ram, and 30 TB of storage
* Supports automatic replication scenarios, such as from a Cloud SQL primary instance, an external primary instance, and external MySQL instances
* Supports managed backups, so backed up data is securely stored and accessible if a restore is required
* Cost of an instance covers seven backups
* Encrypts customer data when on Google's internal networks and when stored in database tables, temp files, and backups
* Includes a network firewall, which controls network access to each database instance
* Accessible by other Google Cloud services and even external services
* Can be used with AppEngine using standard drivers like Connector/J for java or MySQL DB for Python
* Compute Engine instances can be authorized to access Cloud SQL instances and configure it to be in the same zone as your VM
* Also supports other apps and tools that you might use like SQL Workbench

### Cloud Spanner
* Fully managed relational database service that scales horizontally, is strongly consistent, speaks SQL
* Especially suited for apps that require a SQL relational db mgmt system with joins and secondary indexes, built-in high availability, strong global consistency, database sizes that exceed 2TB, and high numbers of IO ops per second

### Firestore
* Flexible, horizontally scalable, NoSQL database for mobile, web, and server development
* Data is stored in documents and then organized into collections
* Documents can contain complex nested objects in addition to sub-collections
* NoSQL queries can then be used to retrieve individual specific documents or to retrieve all the documents in a collection that match your query parameters
* Indexed by default, so query performance is proportional to the size of the result set, not the dataset
* Uses data sync to update data 
* Designed to make simple one-time fetch queries - it caches data that an app is actively using, so the app can write, read, listen to, and query data even if the device is offline. When the device comes back online, Firestore syncs any local changes back to Firestore
* Charges for each document read, write, and delete that you perform 
* Queries are also charged with the rate of one document read per query, whether it returns data or not
* Charged for the amount of storage your data consumes and for certain network bandwidth used to access your data
* Ingress is currently free and in many cases so is egress
* Has a free quota per day of 50k document reads, 20k document writes, 20k document deletes, and 1GB of stored data

### Cloud Bigtable
* NoSQL big data database service
* Designed to handle massive workloads at consistent low latency and high throughput
* Great choice for both operational and analytical apps including IoT, user analytics, and financial data analysis
* Pick Bigtable if they're working with more than one TB of semi-structured data or structured data
* Can be streamed through popular stream processing frameworks

### Comparing Storage Options
* Cloud Storage: Storing immutable blobs larger than 10 MB. Capacity in petabytes and max unit size is 5TB per object
* Cloud SQL: Full SQL support for an online transaction processing system. Web frameworks and existing apps. Capacity up to 30,720GB
* Spanner: Full SQL support for an online transaction processing system. Horizontal scalability. Large-scale db apps that are larger than 2TB. Capacity in petabytes
* Firestore: Massive scaling and predictability together with real-time query results and offline query support. Capacity in TB and max unit size 1MB per entity
* Cloud Bigtable: Storing large amount of structured objects. Doesn't support SQL queries and multi-row transactions. Analytical data with heavy read and write events. Capacity in petabytes and max unit size is 10MB p/cell and 100MB p/row
* BigQuery not mentioned because it sits on the edge between data store and data processing. Usual reason to store data in BigQuery so you can use its big data analysis and interactive querying. Not purely a data storage product
