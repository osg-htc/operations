GWMS Frontend Service Level Agreement
================================

Service Name(s)
---------------

GWMS Frontend

Description
-----------

The GlideinWMS Frontend is responsible for monitoring a GWMS HTCondor pool, and submits pilot submission requests to the factory to compute sites based on user demand. There is usually one frontend per HTCondor Pool for a given scientific community.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

The frontend generates credentials required to talk to the factory, manage the HTCondor pool, and submit to Compute Entrypoints. These can either be GSI, or IDTOKENS for pool credentials, and SciTokens for CE submission credentials. The Frontend forwards CE and pilot credentials to the factory by sending encrypted classads in the Factory Collector.

Service Availability
--------------------

#### Availability Definition

`https://HOSTNAME/vofrontend/monitor/frontend_status.xml` is accessible and updated time is < 20 min from now

#### Target Availability: 95%
