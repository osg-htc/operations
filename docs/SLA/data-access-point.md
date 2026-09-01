Access Point Service Level Agreement
================================

Service Name(s)
---------------

Access Point

Description
-----------

The Access Point is a HTCondor-based service that runs a submit host, and manages the queue of user jobs submitted to a HTCondor pool.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

The Schedd is usually on a host that requires interactive logins for users. Access is generally provided via SSH. The Schedd authenticates with other daemons in the HTCondor pool with either GSI or IDTOKENS.

Service Availability
--------------------

#### Availability Definition

   - condor_q returns successfully
   - The condor_schedd process is able to post a SchedD ad into its primary collector

#### Target Availability: 95%
