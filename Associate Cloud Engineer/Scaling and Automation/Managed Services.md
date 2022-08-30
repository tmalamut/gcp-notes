# Managed Services

### BigQuery
* BigQuery is Google Cloud's serverless, highly scalable, and cost-effective cloud data warehouse
* Fully managed
* Petabyte scale
* SQL interface
* Since it's managed, can focus on uncovering meaningful insights without the need for a database admin

### Dataflow
* Use to execute a wide variety of data processing patterns
* Serverless, fully managed data processing
* Batch and stream processing with autoscale
* Open source programming using Beam
* Intelligently scale to millions of QPS (queries per second)

### Dataprep
* Use to visually explore, clean, and prepare data for analysis and machine learning
* Serverless, works at any scale
* Suggests ideal data transformation
* Focus on data analysis
* Can be leveraged to prepare raw data from BigQuery, Cloud Storage, or a file upload before ingesting it into a transformational pipeline like Dataflow
* The refined data can then be exported to BigQuery or Cloud Storage for analysis and machine learning

### Dataproc
* Is a service for running Apache Spark and Apache Hadoop clusters
* Low cost (per-second, preemptible)
* Super fast to start, scale, and shut down
* Integrated with GCP
* Managed service
* Simple and familiar
* If you have dependencies, or specific tools, or packages in the Hadoop or Spark ecosystem, use Dataproc
* Is not serverless because you're able to view and manage the underlying instances

