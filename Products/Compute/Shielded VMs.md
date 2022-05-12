# Shielded VMs

### Definitions
* Hardened VMs
* Offers verifiable integrity of your Compute Engine VM instances, so you can be confident your instances haven't been compromised by boot-or kernel-level malware of rootkits.
* Verifiable integrity is achieved through the use of the following features:
    * Secure Boot: Helps ensure that the system only runs authentic software by verifying the digital signature of all boot components, and halting the boot process if signature verification fails. 
    * Virtual Trusted Platform Module (vTPM): Is a virtualized trusted platform module, which is a specialized computer chip you can use to protect objects, like keys and certificates, that you use to authenticate access to your system.
        * Enables Measured Boot by performing the measurements needed to create a known good boot baseline, called the integrity policy baseline.
    * Integrity Monitoring: Helps you understand and make decisions about the state of your VM instances.
        * Relies on the measurements created by Measured Boot, which use platform configuration registers to storm information about the components and component load order of both the integrity policy baseline (a known good boot sequence), and the most recent boot sequence.