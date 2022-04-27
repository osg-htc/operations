General Service Level Agreement
===============================

Executive Summary
-----------------

This service level agreement (SLA) is between OSG and its Stakeholders, and applies to all centrally provided OSG production services. A specific SLA exists for each service type; it will list specific services covered by this type, provide a brief description, link to this document, provide specific security considerations, and define service-specific availability metrics.

Owners
------

This SLA is owned by OSG Operations and will be reviewed and agreed upon by the OSG Executive Team and service Stakeholders. The ultimate responsibility for abiding to the SLA lies with the OSG Executive Director and Technical Director. 

Service Target Response Priorities and Response Times
-----------------------------------------------------

This section deals with unplanned outages. Please see [Planned Service Changes](#planned-service-changes) for information on planned maintenance outages.

| Severity | Description | Response Time | Resolution Time | Escalation Rate |
| -------- | ----------- | ------------- | --------------- | --------------- |
| High | The issue prevents any use of the service | Within 4 business hours | 2 business days | 2 business days |
| Elevated | The issue prevents some acceptable uses | Within 2 business days | 5 business days | 5 business days |
| Normal | The issue causes degraded performance | Within 3 business days | 30 business days | 30 business days |

**Services generally operate all the time, but support will be within business hours (9 a.m. to 5 p.m.) in the timezone of the host institution. The exception is for security incidents.**

Escalation Procedure
--------------------

Once a service can not be restored within the SLA Resolution Time specified, it automatically escalates. Subsequent levels escalate every period as defined in the Escalation rate in the response table above. Any issue starts at escalation level 1.

| Escalation Level | OSG Contact |
| ---------------- | ----------- |
| 1st | Service Owner |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Technical Director and Executive Director |

Any ongoing issues will be discussed at the weekly [Operations](/#weekly-operations-meetings) and [Production](https://osg-htc.org/production/#weekly-production-meetings) meetings. "High" and possibly "Elevated" level issues will in addition require more frequent meetings of the appropriate set of people to resolve the issue in a timely manner.

Service Availability and Outages
--------------------------------

The Operations team will strive for monthly availability target percentages as declared in service specific SLAs, where availability is also defined per service. If service availability falls below monthly targets as monitored on two consecutive months, a root cause analysis and service plan will be submitted to the OSG Executive Team. This plan specifies actions to restore the service to the level of availability as specified in the SLA.

Off-Hours Support Procedures
----------------------------

OSG is presently not structured to commit to provide off-hours support. Accordingly, any off-hours support that may be provided is based on staff going beyond their agreed-upon responsibilities.

Planned Service Changes
-----------------------

The Operations team reserves the right to change the service based on its needs. No change will occur without notifying Stakeholders at least 5 business days in advance via the operations meeting and the operations email list. This includes both downtimes, as well as changes in functionality that do not substantially change the nature of the service. More substantial changes require more planning and longer lead times.

Requests for Service Enhancements
---------------------------------

Stakeholders may request service enhancements via standard ticketing procedures. It is up to the Operations team to assess the impact of the requested changes and assign appropriate planning and review.

Customer Problem Reporting
--------------------------

Service problems should be reported immediately by opening a ticket:

   - Either directly at <https://support.opensciencegrid.org>
   - Or by emailing a description to <help@opensciencegrid.org>

Responsibilities
----------------

#### Customer Responsibilities

Service customers agree to:

   - Use the service as intended and only for OSG approved work.
   - Alert the Operations team if they are going to use the service in a non-standard way, including testing or anticipated significant increases in usage.
   - Contact the Operations team by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section above if they encounter any service issues.
   - Be willing and available to provide information in a timely manner consistent with the promised [Resolution Times](#service-target-response-priorities-and-response-times) listed above.

#### OSG Responsibilities

   - Create and add appropriate documentation for appropriate use of the service.
   - Meet response times associated with the priority assigned to Customer issues.
   - Maintain appropriately trained staff.
   - The OSG and Operations team are not responsible to meet target Resolution Times if a customer does not provide sufficient feedback.
   - Log and track all customer requests for service through the OSG ticketing system.
   - Announce planned changes to stakeholders in accordance with the [Planned Service Changes](#planned-service-changes) section above and try to minimize adverse effects on stakeholders.

SLA Change Procedure
--------------------

This SLA will remain valid unless a change or update is requested by the OSG Operations Coordinator, the OSG Executive Team, or Stakeholders. Any disagreements between OSG Executive Team and Stakeholders about desired changes or implementation of these SLAs will get resolved via the OSG Council.
