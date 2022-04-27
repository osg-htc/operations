HTCSS Pool Central Manager Service Level Agreement
================================

Service Name(s)
---------------

Central Manager

Description
-----------

The  Central Manager is the HTCondor service that represents a HTCondor pool. It is the central database of available resources and users who submit to them. Submit hosts communicate user information to the Collector from the VO Schedds. When pilots or containers claim resources, they connect to the collector to describe the claimed machine. HTCondor can then match user jobs to resources using the normal matchmaking mechanisms.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

Schedds and pilots are authenticated and authorized to write ads to the collector using GSI or IDTOKENS.

Service Availability
--------------------

#### Availability Definition

   - The collector responds to condor_status queries
   - The negotiator process posts submitter priority summaries in the collector

#### Target Availability: 95%
