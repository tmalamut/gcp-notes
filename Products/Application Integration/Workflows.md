# Workflows

### Definitions
* HTTP services orchestration
* A fully-managed orchestration platform that executes services in an order that you define: a workflow.
* Can combine services including custom services hosted on Cloud Run or Cloud Functions, Google Cloud services such as Cloud Vision API and BigQuery, and any HTTP-based API.

### When To Use
* Example use cases:
    * Perform a sequence of operations across multiple systems, waiting for all operations ot complete
        * Send newly uploaded files to Cloud Vision AI, then write tags into Firestore.
    * Automate line-of-business workflows
        * Track an order from request to fulfillment