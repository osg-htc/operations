OSDF Cache Service Level Agreement
================================

Service Name(s)
---------------

ODSF (Open Science Data Federation) Cache

Description
-----------

Clients contact the closest Cache to access data from the OSDF federation. This server caches fetched files to reduce transfer overhead over the WAN

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

When clients use SciTokens to authenticate with the cache, the bearer token is passed to the cache (which may subsequently use it to impersonate the client to communicate with the origin).

Service Availability
--------------------

#### Availability Definition

Can successfully read a test file through the Cache server

#### Target Availability: 95%
