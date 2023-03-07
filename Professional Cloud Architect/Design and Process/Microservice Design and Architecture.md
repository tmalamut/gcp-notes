# Microservice Design and Architecture

### Microservices
* Microservices divide a large program into multiple smaller, independent services
* Monolithic applications implement all features in a single code base with a database for all data
* Microservices have multiple code bases, and each service manages its own data
* Pros of microservice architecture
    * Easier to develop and maintain
    * Reduced risk when deploying new versions
    * Services scale independently to optimize use of infrastructure
    * Faster to innovate and add new features
    * Can use different languages and frameworks for different services
    * Choose the runtime appropriate to each service
* Cons of microservice architecture
    * Increased complexity when communicating between services
    * Increased latency across service boundaries
    * Concerns about securing inter-service traffic
    * Multiple deployments
    * Need to ensure you don't break clients as versions change
    * Must maintain backward compatibility with clients as the microservice evolves
* The key to architecting microservice applications is recognizing service boundaries
    * Decompose apps by feature to minimize dependencies
        * Reviews service
        * Orders service
        * Products service
        * Etc
    * Organize services by architectural layer
        * Web, Android, and iOS user interfaces
        * Data access services
    * Isolate services that provide shared functionality
        * Authentication service
        * Reporting service
        * Etc.
* Stateful services have different challenges than stateless ones
    * Stateful services manage stored data over time
        * Harder to scale
        * Harder to upgrade
        * Need to backup
    * Stateless services get their data from the environment or other stateful services
        * Easy to scale by adding instances
        * Easy to migrate to new versions
        * Easy to administer
* Avoid storing shared state in-memory on your servers
    * Requires sticky sessions to be setup in the load balancer
    * Hinders elastic autoscaling
* Store state using backend storage services shared by the frontend server
    * Cache state data for faster access
    * Take advantage of Google Cloud-managed data services
        * Firestore, Cloud SQL, etc. for state
        * Memorystore for caching
* General solution for large-scale cloud-based systems
    * Use DNS and HTTP(S) load balancing to get requests from users
    * Use internal load balancers to communicate between frontend and backend services
    * Many small stateless servers for scalability and fault tolerance
    * Isolate stateful servers
* Twelve-Factor App is a set of best practices for building web or software-as-a-service
    1. One codebase tracked in revision control, many deploys
          * Use a version control system like Git
          * Each app has one code repo and vice versa
    2. Explicitly declare and isolate dependencies
         * Use a package manager like Maven, Pip, NPM to install dependencies
         * Declare dependencies in your code base
    3. Store config in the environment
         * Don't put secrets, connection strings, endpoints, etc., in source code
         * Store those as environment variables 
    4. Treat backing services as attached resources
         * Databases, caches, queues, and other services are accessed via URLs
         * Should be easy to swap one implementation for another
    5. Strictly separate build and run stages
        * Build creates a deployment package from the source code
        * Release combines the deployment with configuration in the runtime environment
        * Run executes the application
    6. Execute the app as one or more stateless processes
        * Apps run in one or more processes
        * Each instance of the app gets its data from a separate database service
    7. Export services via port binding
        * Apps are self-contained and expose a port and protocol internally
        * Apps are not injected into a separate server like Apache
    8. Scale out via the process model
        * Because apps are self-contained and run in separate process, they scale easily by adding instances
    9. Maximize robustness with fast startup and graceful shutdown
        * App instances should scale quickly when needed
        * If an instance is not needed, you should be able to turn it off with no side effects
    10. Keep development, staging, and production as similar as possible
         * Container systems like Docker makes this easier
         * Leverage infrastructure as code to make environments easy to create
    11. Treat logs as event streams 
         * Write log messages to standard output and aggregate all logs to a single source
    12. Run admin/management tasks as one-off processes
        * Admin tasks should be repeatable processes, not one-off manual tasks
        * Admin tasks shouldn't be a part of the app









### REST and APIs