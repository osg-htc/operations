Data Access Point Service Level Agreement
=========================================

Service Name(s)
---------------

Data Access Point (DAP)

Description
-----------

The Data Access Point is a service for placing workloads and managing their storage and I/O capacity.
From a Data Access Point, users have the ability to access a range of capacity and place objects across a data federation.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

The Data Access Point is often on a host that requires interactive logins for users.
Access is generally provided via SSH.
The Access Point authenticates with HTCSS daemons through IDTOKENS and may generate SciTokens for users to access
objects available through a data federation.

Service Availability
--------------------

#### Availability Definition

   - condor_q returns successfully
   - The condor_schedd process is able to post a SchedD ad into its primary collector

#### Target Availability: 95%
