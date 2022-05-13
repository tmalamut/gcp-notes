# Cloud Scheduler

### Definitions
* Managed cron job service.
* Set up scheduled units of work ot be executed at defined times or regular intervals.
    * Work units known as cron jobs.
* Each cron job created using Cloud Scheduler is sent to a target according to a specified schedule, where the work for the task is accomplished.
* Target must be one of these types:
    * Publicly available HTTP/S endpoints
    * Pub/Sub topics
    * App Engine HTTP/S apps

### When To Use
* Typical use cases:
    * Sending out a report email on a daily basis
    * Updating some cached data every 10 minutes
    * Updating some summary information once an hour.