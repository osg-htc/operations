OSDF Core Service Level Agreement
=================================

Service Name(s)
---------------

ODSF (Open Science Data Federation) Redirector, ODSF Monitor Collector, ODSF Shoveler

Description
-----------

The Redirector routes cache requests to be served by the respective data origin that contains the requested file. The Monitor is used to collect transfer accounting data. The Shoveler forwards transfer accounting data from the OSG Message Bus to the WLCG Message Bus

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

If the client uses a SCITOKEN to retrieve a file, the cache may contact the redirector with the SCITOKEN to determine the origin that holds the file.  The Monitoring Collector receives messages from XRootD caches that may include DNs, though not the actual certificates and not SCITOKENS.  The monitoring collector has credentials to talk to the OSG Message Bus.  The shoveler has credentials to talk to the OSG Message Bus, and the WLCG Message Bus.

Service Availability
--------------------

#### Availability Definition

   - Redirector: Able to redirect a known file
   - Monitoring Collector: Outgoing queues in message bus is above 1/sec, or prometheus endpoint is responding
   - Shoveler: Message bus queue for ingestion by the shoveler stays beneath 10,000 queued messages


#### Target Availability: 95%
