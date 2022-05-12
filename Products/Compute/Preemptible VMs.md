# Preemptible VMs

### Definitions
* Short-lived compute instances.
* Are available at a much lower price - a 60-90% discount - compared to the price of standard VMs.
* Compute Engine might stop (preempt) these instances if it needs to reclaim the compute capacity for allocation to other VMs.
* Preemptible instances use excess Compute Engine capacity, so their availability varies with usage.

### When To Use
* If your apps are fault-tolerant and can withstand possible instance preemptions, then preemptible instances can reduce your Compute Engine costs significantly.
* Ex: Batch processing jobs can run on preemptible instances. If some of those instances stop during processing, the job slows but does not completely stop.
    * Preemptible instances complete your batch processing tasks without placing additional workload on your existing instances and without requiring you to pay full price for additional normal instances.