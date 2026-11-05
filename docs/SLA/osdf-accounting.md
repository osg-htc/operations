OSDF Accounting Service Level Agreement
=======================================

OSDF (Open Science Data Federation) Monitor Collector, OSDF Shoveler

Description
-----------

-  The Monitor is used to collect transfer accounting data
-  The Shoveler forwards transfer accounting data from the OSG Message Bus to the WLCG Message Bus

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

-   The Monitoring Collector receives messages from XRootD caches that may include DNs, though not the actual
    certificates and not SciTokens.
-   The monitoring collector has credentials to talk to the OSG Message Bus. The shoveler has credentials to talk to
    the OSG Message Bus, and the WLCG Message Bus.

Service Availability
--------------------

#### Availability Definition

   - Monitoring Collector: Outgoing queues in message bus is above 1/sec, or prometheus endpoint is responding
   - Shoveler: Message bus queue for ingestion by the shoveler stays beneath 10,000 queued messages

#### Target Availability: 95%
