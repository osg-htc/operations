Message Broker Service Level Agreement
======================================

Service Name(s)
---------------

Message Broker

Description
-----------

This service allows short, text based messages to be exchanged between OSG operated computers. Uses include transport of accounting information to GRACC and network performance metrics to perfsonar. Service subscribers access queues to exchange data using point-to-point or publish and subscribe patterns. See [the Wikipedia article on message queueing services](https://en.wikipedia.org/wiki/Message_queuing_service) for further discussion.

The OSG uses a commercial vendor which provides their own [SLA](https://www.cloudamqp.com/sla.html). However, their SLA does not cover "overuse of resources," which is a common reason for downtime of the message broker.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

All data transmitted to or by the service shall be considered disclosable without condition. Security of the message broker is handled by the commercial vendor. Accounts / passwords are administered by the OSG.

Service Availability
--------------------

#### Availability Definition

Messages can be successfully posted and received.

#### Target Availability: 95%
