GWMS Factory Service Level Agreement
====================================

Service Name(s)
---------------

GWMS Factory

Description
-----------

The GlideinWMS Factory is responsible for serving GWMS Frontend requests and submitting pilots to compute sites on behalf of the respective science communities each Frontend supports based on user demand. Pilots are most typically submitted to sites through their respective Compute Entrypoints.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

Frontends register to the Factory using HTCondor supported security mechanisms. The current supported authorization and authentication method is GSI based. A registered frontend is granted access to write requests in the form of HTCondor Classads to the Factory Collector. The factory receives submit credentials from the frontend through encrypted HTCondor classads; the factory can impersonate the identities from the frontend. The factory submits on a Frontend’s behalf to Compute Entrypoints using either GSI or SciTokens.

Service Availability
--------------------

#### Availability Definition

Querying factory collector successfully returns, LastHeardFrom ad is < 6h from now

#### Target Availability: 95%
