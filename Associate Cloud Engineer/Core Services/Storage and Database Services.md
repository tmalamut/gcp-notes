# Storage and Database Services

### Cloud Storage
* Cloud Storage is an object storage service
    * Website content
    * Storing data for archiving and disaster recovery
    * Distributing large data objects to users via direct download
* Key features
    * Scalable to exabytes
    * Time to first byte in milliseconds
    * Very high availability across all storage classes
    * Single API across storage classes
* Storage classes
    * Standard
        * "Hot" data and/or stored for only brief periods of time like data-intensive computations
        * No minimum storage duration
        * No retrieval cost
        * Availability SLA: 99.95% for multi/dual and 99.90% for region
    * Nearline
        * Infrequently accessed data like data backup, long-tail multimedia content, and data archiving
        * 30 day minimum storage duration
        * $0.01 per GB retrieval cost
        * Availability SLA: 99.90% for multi/dual and 99.00% for region
    * Coldline
        * Infrequently accessed data that you read or modify at most once a quarter
        * 90 day minimum storage duration
        * $0.02 per GB retrieval cost
        * Availability SLA: 99.90% for multi/dual and 99.00% for region
    * Archive
        * Data archiving, online backup, and disaster recovery
        * 365 day minimum storage duration
        * 0.05 per GB retrieval cost
        * No availability SLA
* Buckets
    * Naming requirements (globally unique name)
    * Cannot be nested
* Objects
    * Inherit storage class of bucket when created
    * No minimum size; unlimited storage
* Access
    * gsutil command
    * (RESTful) JSON API or XML API
* Changing default storage classes
    * Default class is applied to new objects
    * Regional bucket can never be changed to multi/dual-region
    * Multi-regional bucket can never be changed to regional
    * Objects can be moved from bucket to bucket
    * Object Lifecycle Management can manage the classes of objects
* Access control
    * IAM, ACLs (Access Control Lists), Signed URL, and Signed Policy Document can be used together

### Cloud Storage Features
* Customer-supplied encryption key (CSEK)
    * Use your own key instead of Google-managed keys
* Object Lifecycle Management
    * Automatically delete or archive objects
* Object Versioning
    * Maintain multiple versions of objects
* Directory synchronization
    * Syncs a VM directory with a bucket
* Object change notification
* Data import
* Strong consistency
* Object Versioning supports the retrieval of objects that are deleted or overwritten
    * Objects are immutable
    * Object Versioning:
        * Maintain a history of modifications of objects
        * List archived versions of an object, restore an object to an older state, or delete a version
* Object Lifecycle Management policies specify actions to be performed on objects that meet certain rules
    * Examples:
        * Downgrade storage class on objects older than a year
        * Delete objects created before a specific date
        * Keep only the 3 most recent versions of an object
    * Object inspection occurs in asynchronous batches
    * Changes can take 24 hours to apply
* Object change notification can be used to notify an app when an object is updated or added to a bucket
    * Recommended: Pub/Sub Notifications for Cloud Storage
* Data import services
    * Transfer Appliance: Rack, capture, and then ship your data to Google Cloud
    * Storage Transfer Service: Import online data (another bucket, an S3 bucket, or web source)
    * Offline Media Import: Third-party provider uploads the data from physical media
* Provides strong global consistency

### Choosing A Storage Class
* If the data is structured, consider a structured database service
* If the data is unstructured:
    * Read < 1 per year: Archive Storage
    * Read < 1 per 90 days: Coldline Storage
    * Read < 1 per 30 days: Nearline Storage
    * Sooner: Standard Storage
* Choose location and type by balancing latency, availability, and bandwidth costs for data consumers

### Filestore
* Filestore is a managed file storage service for applications
* Fully managed network attached storage (NAS) fo Compute Engine and GKE instances
* Predictable performance
* Full NFSv3 support
* Scales to 100s of TBs for high-performance workloads
* Use cases:
    * App migration
    * Media rendering
    * Electronic Design Automation (EDA)
    * Data analytics
    * Genomics processing
    * Web content management

### Cloud SQL
* Cloud SQL is a fully managed database service (MySQL, PostgreSQL, or Microsoft SQL Server)
    * Patches and updates automatically applied
    * You administer MySQL users
    * Cloud SQL supports many clients
        * gcloud sql
        * App Engine, Google Workspace scripts
        * Apps and tools
            * SQL Workbench, Toad
            * External apps using standard MySQL drivers
* Cloud SQL Instance
    * Choice:
        * MySQL 5.6, 5.7 (default), or 8.0
        * PostgreSQL 9.6, 10, 11, 12, 13 (default), or 14
        * Microsoft SQL Server 2017 or 2019 (Standard default)
    * Performance:
        * 64 TB of storage
        * 60,000 IOPS
        * 624 GB of RAM
        * Scale out with read replicas
* Cloud SQL Services
    * HA configuration
        * In HA configuration, within a regional instance, the configuration is made up of a primary instance and standby instance
        * Thru synchronous replication to each zones' persistent disk, all writes made to the primary instance are replicated to disks in both zones before a transaction is reported as committed
        * In the event of an instance or zone failure, the persistent disk is attached to the standby instance, and it becomes the new primary instance
            * This process is called a failover
    * Backup service
    * Import/export
    * Scaling
        * Up: Machine capacity
        * Out: Read replicas
* Connecting to a Cloud SQL instance
    * Choosing a connection type to your Cloud SQL instance will influence how secure, performant, and automated it will be
    * If you're connecting an app that's hosted within the same Google Cloud project as your Cloud SQL instance, and it's collocated in the same region, choose the Private IP connection
    * If the app is hosted in another region or project, or if you're trying to connect to your instance from outside of Google Cloud, you have 3 options
        * Recommend using Cloud SQL Proxy, which handles authentication, encryption, and key rotation for you
        * If you need manual control over the SSL connection, you can generate and periodically rotate the certificates yourself
        * Otherwise, you can use an unencrypted connection by authorizing a specific IP address to your SQL Server over its external IP address
* Choosing Cloud SQL
    * Memorystore provides a fully-managed in-memory data store service for workloads requiring microsecond response times, or that of large spikes in traffic, as seen in gaming environments and real-time analytics
    * If you don't need an in-memory data store, but your use case is relational data used primarily for analytics, choose BigQuery
    * If your relational data workoad isn't analytics and a database with ACID properties is a requirement, the choice lies between Cloud Spanner and Cloud SQL
        * If you don't need horizontal scaling or a globally available system, Cloud SQL is a cost-effective solution

### Cloud Spanner
* Cloud Spanner combines the benefits of relational database structure with non-relational horizontal scale
    * Scale to petabytes
    * Strong consistency
    * High availability
    * Used for financial and inventory apps
    * Monthly uptime
        * Multi-regional: 99.999%
        * Regional: 99.99%
* A Cloud Spanner instance replicates data in zones which can be within one region or across several regions
* The replication of data will be synchronized across zones using Google's global fiber network

### Firestore
* Firestore is a NoSQL document database
    * Simplifies storing, syncing, and querying data
    * Mobile, web, and IoT apps at global scale
    * Live sync and offline support
    * Security features
    * ACID transactions
    * Multi-region replication
    * Powerful query engine   
* Is the next generation of Datastore
    * Datastore mode (new server projects)
        * Compatible with Datastore apps
        * Strong consistency
        * No entity group limits
    * Native mode (new mobile and web apps)
        * Strongly consistent storage layer
        * Collection and document data model
        * Real-time updates
        * Mobile and Web client libraries
* If schema might change and need an adaptable database, go with Firestore

### Cloud Bigtable
* Cloud Bigtable is a NoSQL big data database service
    * Petabyte-scale
    * Consistent sub-10ms latency
    * Seamless scalability for throughput
    * Learns and adjusts to access patterns
    * Ideal for Ad Tech, Fintech, and IoT
    * Storage engine for ML apps
    * Easy integration with open source big data tools
* Stores data in massively scalable tables, each is sorted in key-value map
* The table is composed of rows, which typically describes a single entity in columns which contain individual values for each row
* Each row is indexed by a single row key and columns that are related to one another are typically grouped together into a column family
* Each column is identified by a combination of the column family and a column qualifier, which is a unique name within the column family
* Each row column intersection can contain multiple cells or versions at different time stamps providing a record of how the stored data has been altered over time
* Tables are sparse - if a cell doesn't contain any data, it doesn't take up any space
* Processing is handled separately from the storage

### Memorystore
* Memorystore is a fully managed Redis service
    * In-memory data store service
    * Focus on building great apps
    * High availability, failover, patching, and monitoring
    * Sub-ms latency
    * Instances up to 300 GB
    * Network throughput of 12 Gbps
    * Easy Lift-and-Shift
