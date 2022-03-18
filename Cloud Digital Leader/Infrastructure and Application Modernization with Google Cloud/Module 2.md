### Cloud Change Patterns
* If an organization wants to take a relatively conservative approach to modernizing apps with the cloud, they might take a move first then change approach.
    * Essentially a lift and shift program for selected apps.
* If an organization wants to take a more aggressive approach, they can re-architect apps first to make them more cloud ready before migrating them.
    * Referred to as a greenfield strategy.
* A brownfield strategy is to invent a new app in the cloud environment that will replace an existing legacy app that remains on-prem.

### Challenges In App Development
* Often, an app has been built with a monolithic architecture
    * Means that as it's updated over time, its code base becomes bloated, making it difficult to change something without breaking something else.
* When building new apps or modernizing existing ones, a microservice architecture can reduce the problems from the monolithic architecture.
    * Involves the separation of a large app into small, loosely coupled services.
    * Code base for each service is modular so it's easy to determine where the code needs to be changed.
    * Each service can be scaled independently depending on its specific requirements.
* Adopting an automated continuous integration and continuous deployment approach (CI/CD) can help you increase your app release velocity and reliability.
    * Can test and roll out changes incrementally instead of making big releases with multiple changes.
    * Enables you to lower the risk of regressions, debug issues quickly, and roll back to the last stable build if necessary.
    * Can update apps without interrupting services to your users.

### Google Kubernetes Engine
* Kubernetes is an open source container orchestration system for automating computer app deployment, scaling, and management.
* Enables rapid app development and iteration.

### App Engine
* App Engine is a platform for building scalable web apps and mobile backends. 
* Manages the hardware and networking infrastructure required to run your code.
* During deployment, will scale your app automatically in response to the amount of traffic it receives so you only pay for the resources you use.
* Can run multiple versions to test new features.
  