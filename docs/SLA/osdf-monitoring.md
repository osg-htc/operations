OSDF Monitoring Service Level Agreement
================================

Service Name(s)
---------------

OSDF (Open Science Data Federation) Monitoring

Description
-----------

A server that send and receives the monitoring data for OSDF


General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

Service Availability
--------------------

#### Availability Definition

 - Monitoring Collector: Outgoing queues in message bus is above 1/sec, or prometheus endpoint is responding
 - Shoveler: Message bus queue for ingestion by the shoveler stays beneath 10,000 queued messages

#### Target Availability: 95%
