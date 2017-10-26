# RabbitMQ Message Bus Service Level Agreement

## About This Document
This document details a service level agreement which outlines production expectations for event1.grid.iu.edu and defines general support infrastructure for the service.



## Executive Summary
This SLA is an agreement between OSG and OSG Stakeholders pertaining to the operation of the OSG RabbitMQ message bus.
This service allows short, text based messages to be exchanged between OSG operated computers. Anticipated uses include 
transport of accounting information to GRACC and network performance metrics to perfsonar. An overall service availability
of 95% is requested, a level that reflects the current understanding of the frequency of external events causing service failures or degradation.

## Owners
This SLA is owned by IU OSG Operations (IU-OPS). It will be reviewed by and agreed upon by the OSG Executive Team.

## Service Name and Description
### Name
OSG RabbitMQ Message Bus

### Description
The grid-facing component of this service available for use by all OSG VOs and service providers.
Service subscribers access queues to exchange data using point-to-point or publish and subscribe patterns.
See [the Wikipedia article on message queueing services](https://en.wikipedia.org/wiki/Message_queuing_service) for further discussion.

## Security Considerations
All data transmitted or received via this service 
is subject to the terms of the
[IU privacy policy](https://github.com/opensciencegrid/operations/blob/master/docs/privacy.md).
In particular all data transmitted to or by the service shall be considered disclosable without condition.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Description* | * * | * * | * * |
| This service does not have critical priority  | The issue prevents any use of the service | The issue prevents some acceptable uses of the service | The issue causes degraded performance of the service |
| *Response Time* | * * | * * | * * |
| N/A | Within 4 business hours | Within 2 business days | Within 10 business days |
| *Resolution Time* | * * | * * | * * |
| N/A| Within One Business Day | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is ten (10) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | Two Days | Five Days | Ten Days |

| *Outage Type* | *Description | *Response Time* | *Resolution Time* | *Escalation Rate* |
| Critical | This service does not have critical priority | Within 4 business hours | 2 business days  | 2 business days |
| High     | The issue prevents any use of the service    | Within 2 business days  | 5 business days  | 5 business days |
| Elevated | The issue prevents some acceptable uses      | Within 5 business days  | 10 business days | 10 business days |
| Normal   | The issue causes degraded performance        | Within 10 business days | 30 business days | 30 business days |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Executive Director |

Detailed information on contacts are viewable [in MyOSG](https://oim.grid.iu.edu/oim/resourceedit?id=906).

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and [Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages
The IU-OPS will strive for 95% service availability. If service [availability](http://monitor.grid.iu.edu/availability/avail_month_overview.html) 
falls below 95% monthly as monitored by IU-OPS a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

Availability will be determined by the algorithm documented [here](http://monitor.grid.iu.edu/availability/status/event1/status_stamp.sh).

Users must be aware that during maintenance the system may be rebooted and data loss may result.

## Service Support Hours
This service will operate 24x7, but support will be within business hours. The exception is for security incidents.

## Service Off-Hours Support Procedures
All operational issues should be reported as described in [the Customer Problem Reporting](#customer-problem-reporting) section.

## Requests for Service Enhancements
IU-OPS will provide enhancement capabilities as they are released by the [RabbitMQ](https://www.rabbitmq.com/) project. Requests for customization of the deployed service may be made; IU-OPS has sole discretion as to their implementation and deployment schedule.

IU-OPS will give 1 week of warning prior to any change in the RabbitMQ service version. At any time during this week, Stakeholders are permitted to request a delay for up to 1 week after the originally scheduled upgrade.

   * The exception is for code changes that are deemed critical by IU-OPS staff.
   A critical change can be deployed immediately if approved by the Production or Operations coordinator.
  
IU-OPS will schedule downtimes and configuration changes during normal business hours unless approved by affected stakeholders. This is done so affected stakeholders are always on-hand in case the downtime or changes cause further issues. Exceptions to this are given in the [responsibilities](#Responsibilities) section below.

## Customer Problem Reporting
The IU-OPS provides operators 24x7x365. Message bus related problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/open (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities

   * A RabbitMQ service will be run by IU-OPS and made accessible to registered users.
   * Users of the service are responsible for backup of any data transferred by the system.
   * Individual users agree to use the system in such a way as to allow reasonable access to others.
   * IU-OPS reserves the right to deploy configuration changes (including access limits) without notice as required to allow reasonable access.
   * IU-OPS will coordinate with user groups during maintenace if so requested by the group. It is the responsibilty of the group to have a representitive available if coordination is requested.

## Service Measuring and Reporting
The IU-OPS will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Availability | Monthly | [Web Posting](http://monitor.grid.iu.edu/availability/avail_month_overview.html) | IU-OPS |

## SLA Validity Period

This SLA will be in effect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team, or the Stakeholders.

## References

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 10-24-2017 | Scott Teige | First Draft |

# Appendix A - Approval
| Approved By | Position | Date |
| ----------- | -------- | ---- |
| | | |
