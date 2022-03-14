### Migrating Data to the Cloud
* For most large organizations, a vast amount of data is still stored on-prem or buried on individual computers. 
* If there's data somewhere that isn't being tracked, it's vulnerable to userr attacks and it's unproductive. 
* When you store your data on-prem, you're responsible for the IT infrastructure that supports the collection, security, and processing of that data. Also responsible for maintaining and expanding the capacity of your IT infrastructure. 
* With cloud, can rent space from public cloud providers - this means that your data storage and compute powers are elastic.
    * Elastic meaning it can scale up or down as the data you take increases or decreases.

### Cloud Databases
* A database is an organized collection of data generally stored in tables and accessed electronically from a computer system.
* Data integrity or transactional integrity refers to the accuracy and consistency of data stored in a database.
    * Achieved by implementing a set of rules when a database is first designed, and through ongoing error-checking and validation routines as data is collected.
* Databases allow businesses to roll back transactions to see data history. 
* Another priority is scalability - need to scale to meet demand.
* Most common Google Cloud database services and their benefits:
    * Cloud SQL is a fully-managed Relational Database Management Service, or RDBMS
        * Easily integrates with existing applications and Google Cloud services like Google Kubernetes Engine and BigQuery and buil on the performance innovation in Compute Engine.
        * Is compatible with common database management systems and methodologies. 
        * Offers security, availability, and durability, and store scales automatically when enables. 
        * Might want to use Cloud SQL for databases that serve websites, for operational applications for e-commerce, and to feed into report and chart creation that informs business intelligence.
    * Cloud Spanner is another fully-managed database service, and it's designed for global scale.
        * Data is automatically and instantly copied across regions.
        * Essentially, used for much larger projects than Cloud SQL and is more expensive.

### Cloud Data Warehouses
* While databases store transactional data in an online fashion, data warehouses assemble data from multiple sources, including databases.
* Databases are built and optimized to enable ingesting large amounts of data from many different sources efficiently.
* Data warehouses are built to enable rapid analysis of large and multidimensional datasets.
* Is like a central hub for all business data. Different types of data can be transformed and consolidated into the warehouse so they're useful for analysis.
* Google Cloud data warehouse solution (BigQuery):
    * BigQuery is a fully-managed data warehouse with downtime free upgrades and maintenance and seamless scaling.
    * Allows you to analyze petabytes of data with speed and zero operational overhead. 
    * Is serverless, which means that resources such as compute power are automatically provisioned behind the scenes as needed to run your queries - so businesses do not pay for compute power unless they're actually running a query. 
* Pub/Sub is a service for real-time ingestion of data.
* Dataflow is a service for large scale processing of data.
* The two above services can work together to bring unstructured data into the cloud and transform it into semi-structured data. 
    * Transformed data can then be sent directly from Dataflow to BigQuery, where it becomes immediately available for analysis.

### Cloud Data Lakes
* Another type of data management solution that stores structured, semi-structured, and unstructured data.
* Are repositories for raw data.
* For example, they often hold backup data, which helps businesses build resilience against unexpected harm affecting their data. Essentially, helping to protect from data loss.
* Hold data that is historic and not relevant to day-to-day business operations.
* Google Cloud data lake service (Cloud Storage):
    * A service that enables you to store and serve Binary Large Object, or BLOB data. BLOBs are typically images, audio, or other media objects.
    * Can store unlimited data with no minimum amount required, low latency - you can retrieve your data as often as you'd like - and you can access it from anywhere. 
    * For data that will be accessed less often, offers Nearline, Coldline, and Archive storage classes.
        * Nearline is best for data you don't expect to access more than once per month, such as multimedia file storage or online backups. 
        * Coldline is best for data that you plan to access at most once per 90 days or quarter.
        * Archive is best for data that you plan to access at most once per year, such as archive data or as a backup for disaster recovery. 

### Business Intelligence Solutions
* Looker is a Google Cloud business intelligence solution
    * A data platform that sits on top of an analytics database and makes it simple to describe your data and define business metrics.
    
    
        