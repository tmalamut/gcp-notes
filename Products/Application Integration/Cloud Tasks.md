# Cloud Tasks

### Definitions
* Asynchronous task execution.
* Lets you separate out pieces of work that can be performed independently, outside of your main app flow, and send them off to be processed, asynchronously, using handlers that you create.
* These independent pieces of work are called tasks.
* Ex: You need to update a database as part of processing a user reqest, but updates can be time-consuming. Offloading that detail as a task allows you to return from the request more quickly.
* The offloaded task is added to a queue, which persists the task until it is successfully executed. 

### When To Use
* Typical use cases:
    * Speeding user response times by delegating potentially slow background operations like database updates to a worker (a service which processes tasks).
    * Preserving requests in the context of unexpected production incidents
    * Helping smooth traffic spikes by removing non-user-facing tasks from the main user flow
    * Managing third party API call rates