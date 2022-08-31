# Containers and Kubernetes

### Intro to Containers
* VMs are relatively slow to startup because the entire OS has to boot
* A more efficient way is to implement abstraction at the level of the app and its dependencies 
* Don't have to virtualize the entire machine or the entire OS, but just the user space
    * The user space is all the code that resides above the kernel, includes applications and their dependencies
* Containers are isolated user spaces for running app code
* Are lightweight becuse they don't carry a full OS
* Can be created and shutdown very quickly because you're just starting and stopping the processes that make up the application and not booting up an entire VM and initializing an OS for each app
* You package your code with all the dependencies it needs, and the engine that executes your container, is responsible for making them available at runtime
* Runs the same anywhere

### Containers and Container Images
* An application and its dependencies are called an image
* A container is simply a running instance of an image
* By building software into container images, devs can easily package and ship an app without worrying about the system it will be running on
* Need software to build container images and to run them - Docker is one tool that does both
* Docker is an open source technology that allows you to create and run apps and containers, but it doesn't offer a way to orchestrate those apps at scale like Kubernetes does
* Containers use a varied set of Linux technologies
    * Processes
    * Linux namespaces
    * cgroups
    * Union file systems
* A container image is structured in layers
    * The tool you use to build the image reads instructions from a file called the Container Manifest. For Docker, called a Dockerfile
    * Each instruction in the Dockerfile specifies a layer inside the container image
    * Each layer is read only
    * When a container runs from this image, it will also have a writable ephemeral topmost layer
* Containers promote smaller shared images
    * For example, multiple containers can share the same Ubuntu image
* How can you get containers?
    * Download containerized software from a container registry such as gcr.io
    * Build your own container using the open-source docker command
    * Build your own container using Cloud Build


