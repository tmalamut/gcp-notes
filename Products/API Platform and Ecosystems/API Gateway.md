# API Gateway

### Definitions
* Enables you to provide secure access to your backend services through a well-defined REST API that is consistent across all your services, regardless of the service implementation.
* Clients consume your REST APIs to implement standalone apps, or through any other type of app that can make a request to an HTTP endpoint.
* A consistent API:
    * Makes it easy for developers to consume your services
    * Enables you to change the backend service implementation without affecting the public API
    * Enables you to take advantage of the scaling, monitoring, and security features built into GCP.
* An API is an interface that makes it easy for one app to consume capabilities or data from another app. 
    * By defining stable, simple, and well-documented entry points, APIs enable developers to easily access and reuse app logic built by other devs.
* Web-based services today provide a huge variety of functionality, meaning everything from map, weather, and image services, to games, auctions, and many other service types.
* Service providers have many options for how to implement, deploy, and manage their services.
    * For example, one service might be developed in Java or .NET, while another uses Node.js.
* App developers are the customers of backend services - they consume your services to implement apps.
* To be successful, a service provider must:
    * Authenticate access to the service
    * Secure data transport between clients and the service
    * Protect it from malicious attacks
    * Scale the service as usage increases or decreases
    * Provide the backend ops team with a way to monitor and track usage
    * Track usage to provide accurate billing info

### Use Cases
* Example: REST API that could return info about a book


    | Property      | Value | Description     |
    | :---        |    :----:   |          ---: |
    | URL      |    https://www.mybooksapi.com/books/info    | Return the title, author, and publishing date of a book based on its International Standard Book Number (ISBN).   |
    | HTTP Verb   | GET        | Make a GET request to the API.      |