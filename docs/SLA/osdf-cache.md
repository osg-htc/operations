OSDF Cache Service Level Agreement
================================

Service Name(s)
---------------

OSDF (Open Science Data Federation) Cache

Description
-----------

OSDF clients use the closest Cache to read objects made available through the OSDF.
These objects are stored on the OSDF Cache to serve subsequent requests, reducing load on the OSDF origins.

OSG staff operate a set of geographically distributed OSDF Caches to ensure efficient movement of objects.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

When clients use SciTokens to authenticate with the Cache, the bearer token is passed to the Cache
(which may subsequently use it to impersonate the client to communicate with the origin).

Service Availability
--------------------

#### Availability Definition

-   Web engine, director, and federation health API endpoints report as healthy
-   Client can successfully read a known test file through the Cache

#### Target Availability: 95%
