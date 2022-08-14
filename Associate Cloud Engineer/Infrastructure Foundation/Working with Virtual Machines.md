# Working with Virtual Machines

### Compute Options
* 3 options for creating a VM: Console, Command Line, REST API
* Machine type structure starts at family, then series, then type
    * A machine family is a curated set of processor and hardware configurations optimized for specific workloads
* 4 machine families: General-purpose, Compute-optimized, Memory-optimized, Accelerator-optimized
* General-Purpose Machine Family
    * Has best price performance with the most flexible vCPU to memory ratio and provides features that target most standard and cloud native workoads
    * E2 machine series is suited for day to day computing at a lower cost, especially when there is no app dependencies on specific CPU architecture
    * N2, N2D, N1 provides balanced price/performance across a wide range of VM shapes
    * Tau T2D provides best performance/cost scale-out workloads
* Compute-Optimized Machine Family
    * Has highest performance per core and is optimized for compute-intensive workloads
    * C2 machine series is best fit for ultra high performance for compute-intensive workloads
    * C2D machine series provides largest VM sizes and are best suited for high performance computing
* Memory-Optimized Machine Family
    * Provides the most amount of compute and memory resources of any family offering
    * M1 and M2 provide ultra high-memory workloads for in-memory databases
* Accelerator-Optimized Machine Family
    * Ideal for massively parallel compute unified architecture or CUDA compute workloads such as ML and HPC
    * A2 machine series optimized for HPC
* When to create custom machine type:
    * Requirements fit between the predefined types
    * Need more memory or CPU

### Compute Pricing
* Per-second billing, with a minimum of 1 minute
    * vCPUs, GPUs, and GB of memory
* Resource-based pricing
    * Each vCPU and each GB of memory is billed separately
* Discounts (cannot be combined):
    * Sustained Use
        * Resource-based pricing allows Compute Engine to apply sustained use discounts to all of your predefined machine types usage in a region collectively rather than to individual machine types
    * Committed Use
        * If your workload is stable and predictable, you can purchase a specific amount of vCPUs and memory for a discount off of normal prices in return for committing to a usage term of 1 year or 3 years. 
        * Discount is up to 57% for most machine types or custom machine types. 
        * Discount is up to 70% for memory-optimized machine types
    * Preemptible VM instances
        * Preemptible and Spot VMs are instances that you can create and run at a much lower price than normal instances
        * Compute Engine might terminate (or preempt) these instances if it requires to access those resources for other tasks
        * Can only run for 24 hours at a time, but Spot VMs don't have a max runtime
* Recommendations Engine
    * Notifies you of underutilized instances
    * Provides VM sizing recommendations to help you optimize the resource used of your VM instances
    * When you create a new instance, recommendations for the new instance will appear 24 hours after the instance has been created
 * Free usage limits

### Special Compute Configurations
* Can create monitoring and load balancers that can start up new preemptible VMs in case of a failure
* There are external ways to keep restarting preemptible VMs if you need to
* One major use case for preemptible VMs is running batch processing jobs
* Preemptible instances complete your batch processing jobs w/o placing additional workloads on your existing instances, and w/o requiring you to pay full price for additional normal instances
* Spot VMs can't live-migrate to become standard VMs while they're running or be set to automatically restart when there is a maintenance event
* If you have workloads that require physical isolation from other workloads or VMs in order to meet compliance requirements, you want to consider sole-tenant nodes
* A sole-tenant node is a physical Compute Engine server that is dedicated to hosting VM instances only for your specific project
* If you have existing OS licenses, you can bring them to Compute Engine using sole-tenant nodes while minimizing the physical core usage with the in-place restart feature
* Shielded VMs offer verifiable integrity to your VM instances

### Images
* When creating a VM, you can choose the boot disk image
* Image includes the boot loader, the OS, the file system structure, any preconfigured software and any other customizations
* Can select either public or custom image
* Premium images will have per second charges after a one minute minimum, with the exception of SQL Server images, which are charged after a 10 minute minimum
* Premium images vary with the machine type, but prices are global and don't vary by region or zone
* You can create and use a custom image by preinstalling software that's been authorized for your particular organization
* Can also have the option of importing images from your own premises or workstation or from another cloud provider
* A machine image is a Compute Engine resource that stores all the configuration, metadata, permissions, and data from one or more disks required to create a VM instance
* Can use a machine image in many system maintenance scenarios, such as creation, backup recovery, and instance cloning
* Machine images are the most ideal resources for disk backups, as well as instance cloning and replication

### Disk Options
* Every single VM comes with a single root persistent disk because you're choosing a base image to have it loaded on 
* This image is bootable in that it can attach to a VM and boot from it
* It's durable in that it can survive if the VM terminates
* To have a boot disk survive a VM deletion, you need to disable the "Delete boot disk when instance is deleted" option in the instance properties
* A persistent disk is going to be attached to the VM through the network interface
* Even though it's persistent, it's not physically attached to the machine - this separation of disk and compute allows the disk to survive if the VM terminates
* Can dynamically resize persistent disks even when they're running and attached to a VM
* Can also attach a disk in a read-only mode to multiple VMs - this allows you to share static data between multiple instances which is cheaper than replicating your data to unique disks for individual instances
* Zonal persistent disks offer efficient, reliable block storage
* Regional persistent disks provide durable storage that has synchronously replicated across zones and are great option for high-performance databases and enterprise applications that also require high availability
* When you configure zonal or regional persistent disk, you can select one of the following disk types:
    * Standard persistent disks are backed by a standard hard disk drive
    * Balanced persistent disks are back by solid state drives (alternative to SSD persistent disk)
    * SSD persistent disks are backed by solid state drives
    * Extreme persistent disks are designed for high-end database workloads providing consistently high performance for both random access workloads and throughput
* By default, Compute Engine encrypts all data at rest. Google Cloud handles and manages this encryption w/o any additional actions on your part. If you wanted to control and manage this encryption, you can use either cloud key management service to create and manage key encryption keys, or create and manage your own key encryption keys
* Local SSDs are different from persistent disks as they are physically attached to the VM. Therefore, these disks are ephemeral, but they provide very high IOPS. Currently, you can attach up to eight local SSD disks with 375 gb each resulting in a total of 3 tb
* Local SSDs will survive a reset but not a VM stop or terminate b/c these disks can't be reattached to a different VM
* RAM disk uses tmpfs if you want to store data in memory
* RAM disk will be the fastest type of performance available if you need small data structures
* Best practice for choosing disk:
    * Persistent disk if you don't need the performance, but just the capacity
    * If you have high-performance needs, start looking at SSD options
    * Local SSDs provide even higher performance, but without data redundancy that persistent disks provide
    * RAM disks are very volatile, but they provide the highest performance

### Common Compute Engine Actions
* Every VM instance stores its metadata on a metadata server. 
* The metadata server is particularly useful in combination with startup and shutdown scripts because you can use the metadata server to programmatically get unique information about an instance w/o additional authorization
* For example, you can write a startup script that gets the metadata key-value pair for an instance's external IP address and use that IP address's new script to set up a database
* Because the default metadata keys are the same on every instance, you can reuse your script w/o having to update it for each instance
* Storing and retrieving instance metadata is a very common Compute Engine action
* Best practice is storing the scripts in Cloud Storage
* Another common action is to move an instance to a new zone
* For example, you might do so for geographical reasons or because a zone has been deprecated
* You can move a VM even if one of these following scenarios apply:
    * The VM instance is in a termination stage
    * The VM instance is a Shielded VM that uses UEFI's firmware
* If you move your instance within the same region, you can automate the move by using the 'gcloud compute instances move' command
* To move your VM, you must shutdown the VM, move it to its destination zone or region, and then restart it
* After you move your VM, update any references that you have pointing to the original resource, such as any target VMs or target pools that point to the earlier VM
* If you move your instance to a different region, you need to manually do so by following the process:
    * Snapshot all persistent disks on the source VM
    * Create new persistent disks in destination zone restored from snapshots
    * Create new VM in the destination zone and attach new persistent disks
    * Assign static IP to new VM
    * Update references to VM
    * Delete the snapshots, original disks, and original VM
* Snapshot use cases:
    * Can be used to backup critical data into a durable storage solution to meet app, availability, and recovery requirements
    * Stored in Cloud Storage
    * Used to migrate data between two regions, but can also be used to simply transfer data from one zone to another
        * You might want to minimize latency by migrating data to a drive that can be locally attached in the zone where it is used
    * Transfer data to a different disk type
        * If you want to improve disk perfromance, you could use a snapshot to transfer data from a standard HDD persistent disk to a SSD persistent disk
* Snapshots are only available to persistent disks and not to local SSDs
* Snapshots are different from public images and custom images, which are used primarily to create instances or configure instance templates, in that snapshots are useful for periodic backup of the data on your persistent disks
* Snapshots are incremental and automatically compressed, so you can create regular snapshots on a persistent disk faster and at a much lower cost than if you regularly created a full image of the disk
* Another common Compute Engine action is to resize your persistent disk
* The added benefit of increasing storage capacity is to improve IO performance
* While you can grow disk size, you can never shrink them
    