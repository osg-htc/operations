## Summary Description

Currently OSG Operations performs maintenance (bug fixes, service enhancements, OS updates, etc.)
on a schedule described [here](Tom, Link please). This policy keeps users informed as to activities
in progress and prevents *unexpected* outages. Proposed here is a procedure that maintains the intended
features of the maintenance policy and improves Operations ability to respond quickly to requests and problems.

## The proposed maintenance process

Most (but not all) Operations services exist as multiple *instances* of a virtual machine that performs
the tasks comprising a service. These instances operate, to the extent possible, independently with each
capable of serving the community. The instances are typically labeled, for eample, myosg1 and myosg2
and referred to via DNS aliases simply as myosg. Incomming traffic (e.g. to myosg) is routed to a particular
instance via an [LVS](http://www.linuxvirtualserver.org/) server. It is possible to configure LVS to route
to a specific instance and thus ignore the other.

Proposed here is a modification to the maintenance that exploits this feature. Multihomed services can be
modified at any time as follows: The ITB instance will be modified and the modification described in an announcement.
After a 1 week testing period, the modifications will be propagated to the production machines using
the LVS mechanism to make the service appear uninturrupted. Only multihomed services will be covered by
this change, single homed services will be maintained using the current schedule and policy.

## Multi-homed services

Below is a list of multihomed service to be effected by this proposed change.

   * MyOSG
   * Repo (Software repository)
   * TX (ticket exchange)
   * Ticket
   * Web (serves www.opensciencegrid.org)
   * Cassandra (PerfSonar component)
   * psds (PerfSonar Data Server)
   * perfsonar
   * Condor collector
   * redirector
   
## Single homed services

The following services will be maintained using current procedures.

   * OIM
   * Oasis, Oasis-replica, Oasis-login
   * Display
   * JIRA
   * XD-login
   * OSG-Excede
   
With the exception of JIRA and Display (discussed below) these services, due to constraints of their
purpose or design, cannot be made multihomed.

## Future work

We intend to upgrade the following services to be multihomed.
   * Display, this is beleived to be a trivial task and is scheduled for the next maintenance cycle.
   * JIRA, We are investigating what is involved in making this multihomed. To date there are no known showstoppers.
