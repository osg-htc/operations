OSDF Cache Service Level Agreement
================================

Service Name(s)
---------------

OSDF (Open Science Data Federation) Cache

Description
-----------

OSDF clients use the closest Cache to read objects made available throught the OSDF.
These objects are stored on the OSDF Cache to server subsequent requests, reducing load on the OSDF origins.

OSG staff operate a set of geographically distributed OSDF Caches to ensure efficient movement of objects.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

When clients use SciTokens to authenticate with the cache, the bearer token is passed to the cache
(which may subsequently use it to impersonate the client to communicate with the origin).

Service Availability
--------------------

#### Availability Definition

-   Web engine, director, and federation health API endpoints report as healthy
-   Client can successfully read a known test file through the cache

#### Target Availability: 95%
