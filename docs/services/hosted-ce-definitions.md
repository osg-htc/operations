OSG Hosted CE Definitions
=========================

The OSG provides a Hosted CE service. In general, this document lists what an instance of that service can and cannot do.

Hosted CEs in General
---------------------

#### Benefits

   - The site continues to operate its own batch system according to local considerations;
   - OSG operates the interface between OSG and the site, aka the Hosted CE;
   - To the site, OSG simply looks like a set of user accounts; and
   - OSG uses the accounts to provision site resources for various science user communities, and hence the site has complete control over resource allocation via local policies on the accounts.

#### Prerequisites

In general, the site must operate a working batch system that is accessible via at least one head node; OSG works with HTCondor, Slurm, PBS Pro/Torque, LSF, and Grid Engine. Site operations include hardware and software maintenance, defining and implementing usage policies, monitoring, troubleshooting, etc. These are the same activities to support local users.

In addition, the site:

   - Must communicate with OSG their intent to share resources — in most cases, a meeting between site and OSG staff should be sufficient to discuss goals, plans, etc.;
   - Must meet the technical requirements [on the OSG website](https://opensciencegrid.org/docs/compute-element/hosted-ce/#before-starting), summarized below:
      * The site is willing to add OSG user accounts with inbound SSH access and submit privileges,
      * A mechanism exists for transferring files between the head nodes and worker nodes, and
      * Worker nodes must have outbound Internet access and temporary storage space for jobs.
   - Is strongly encouraged to tell OSG about preferred constraints on resource requests (e.g., per-job limits on CPUs, memory, and storage; overall limits on number of running and idle jobs; submission rates), so that OSG can tailor such requests to better fit the site.

Standard Hosted CE
------------------

A Standard Hosted CE is the default case in which the interaction between OSG and the site is relatively simple and easy to maintain. Most sites fall into this category.

#### Benefits

   - Configuration is limited to basics, so there is less upfront and ongoing work for OSG and the site;
   - OSG maintains and shares mappings from user groups to OSG user accounts on the site, so that the site can — if desired — limit resource allocations to certain groups; and
   - OSG maintains the required OSG configuration on the site’s head node and worker nodes (if the site provides a distribution mechanism to worker nodes, such as a shared file system).

#### Site Responsibilities

In addition to the general prerequisites above, the following apply to a Standard Hosted CE:

   - The site must create and maintain 20 OSG user accounts on a single head node; note that:
      * OSG will access their accounts via SSH using one RSA key for all 20 accounts; and
      * All 20 OSG accounts must be able to submit to the local batch system.
   - The site may control the resources allocated to different OSG user groups by writing and maintaining policies on the OSG user accounts within the batch system.
   - The site provides privilege separation among the OSG user groups via the OSG user accounts and standard Unix privilege separation.
