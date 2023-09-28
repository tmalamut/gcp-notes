# Creating Virtual Machines

### Compute Engine
* Infrastructure as a Service (IaaS) model
* You have a VM and an OS and you choose how to manage it and how to handle aspects such as autoscaling, where you'll configure the rules about adding more VMs in specific situations
* The primary work case of Compute Engine is any general workload, especially an enterprise app that was designed to run on a server infrastructure
* Other services like GKE, which consists of containerized workloads, may not be as easily transferable as what you're used to from on-prem
* Physical servers that you used to run inside Google Cloud's environment with a number of different configs
* Both predefined and custom machine types allow you to choose how much memory and how much CPU you want
* You choose the disk type you want, whether you want to use a persistent disk backed up by standard hard drives or solid-state drives, or local SSds, or Cloud Storage or a mix
* Can even config the networking interface and run a combo of Linux and Windows machines
* Provides several different machine types. If they don't meet your needs, can customize own machine
* Choice of CPU will affect network throughput
* Network throughput scales 2 Gbps per vCPU 
* Theoretical max of 32 Gbps with 16 vCPU or 100 Gbps with T4 or V100 GPUs
* A vCPU is equal to 1 hardware hyper-thread
* Can have Standard, SSD, or Local SSD for storage
* Question is about performance versus cost
* SSDs are designed to give you a higher number of capacity for your dollar
* Local SSDs have even higher throughput and lower latency than SSD persistent disks because they are attached to the physical hardware 
* However, the data you store in a local SSD persists only until you stop or delete the instance
* A Local SSD is used as a swap disk
* Can do regional HTTPS load balancing and network load balancing

### VM Access and Lifecycle
* The creator of an instance has full root privileges on that instance
* On Linux, creator has SSH capability and can use the Cloud Console to grant SSH capability to other users
* On Windows, creator can use the Cloud Console to generate a username and password. After that, anyone who knows the credentials can connect to the instance using a remote desktop protocol (RDP) client
* Lifecycle of VM:
    * When you define all the properties of an instance and click create, the instance enters the provisioning stage
    * Instance moves to the staging state where resources have been acquired and the instances prepared for launch. Compute Engine is adding IP addresses, booting up the system image, and booting up the system
    * After the instance starts running, it will go thru the pre-configured startup scripts and enable SSH or RDP access
    * Can do several things while instances are running. Can live migrate your VM to another host in the same zone instead of requiring your instance to be rebooted 
    * Can also move your VM into a different zone, take a snapshot of the VMs persistent disk, export the system image or reconfig metadata
    * Some actions require you to stop your VM, like if youwant ot upgrade your machine by adding more CPU
* Can use patch management to apply OS system patches across a set of instances


### Test
* Typing here
* 