OSDF Core Service Level Agreement
=================================

Service Name(s)
---------------

OSDF (Open Science Data Federation) Director, OSDF Registry, OSDF Monitor Collector, OSDF Shoveler

Description
-----------

-  The Director redirects clients requesting or writing objects through the OSDF to the relevant cache or origin
-  The Registry keeps a database of all registered OSDF services and their downtimes
-  The Monitor is used to collect transfer accounting data
-  The Shoveler forwards transfer accounting data from the OSG Message Bus to the WLCG Message Bus

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

-   If the client uses a SciToken to retrieve a file, the cache may contact the director with the SciTokento determine
    the origin that holds the file.
-   The Monitoring Collector receives messages from XRootD caches that may include DNs, though not the actual
    certificates and not SciTokens.
-   The monitoring collector has credentials to talk to the OSG Message Bus. The shoveler has credentials to talk to
    the OSG Message Bus, and the WLCG Message Bus.

Service Availability
--------------------

#### Availability Definition

   -  Director:
     -  Web engine health API endpoint reports as healthy
     -  Able to redirect a known test object
   -  Registry
      - Web engine health API endpoint reports as healthy
      - Able to retrieve downtimes
   - Monitoring Collector: Outgoing queues in message bus is above 1/sec, or prometheus endpoint is responding
   - Shoveler: Message bus queue for ingestion by the shoveler stays beneath 10,000 queued messages


#### Target Availability: 95%
