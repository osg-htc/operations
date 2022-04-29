OASIS Repository Service Level Agreement
========================================

Service Name(s)
---------------

OASIS Stratum 0, Oasis Stratum 1, OASIS Login

Description
-----------

The OASIS service provides users with a central location for application software. The content hosted on OASIS can be made available on OSG compute resources. The service consists of three virtual machines, a stratum 0 CERN Virtual Machine File System (CVMFS) server, a stratum 1 replica of the stratum 0 and a node accessible for login by OASIS managers.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

The OASIS stratum 0 server and OASIS stratum 1 are accessible only by OSG Operations and Technology group staff. The OASIS interactive node (oasis-login.opensciencegrid.org) is accessible by OSG Operations and Technology group staff and to registered software managers via gsissh. A person becomes a software manager only by explicit approval of OSG staff within the Topology Database.

The OASIS stratum 1 is publicly available as read-only.

Service Availability
--------------------

#### Availability Definition

CVMFS status returns OK, OASIS stamp status returns OK, CVMFS repo status return OK, service queries return active

#### Target Availability: 95%
