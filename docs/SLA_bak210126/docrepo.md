# OSG Document Repository Service Level Agreement -- *DRAFT*

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.0 | 6-03-2010 | Marcia Teckenbrock | First Draft |



## Executive Summary
This SLA is an agreement between the OSG Communications activity and OSG Management and Stakeholders and describes details of the OSG DocDB service. The OSG DocDB is a document repository used for public documentation related to work in the OSG, including blueprint documents, presentations given at a conference or collaboration meeting or papers published in a journal, among others. The OSG DocDB service runs on hardware at Fermilab that is supported by the Lab and Scientific Core Services Department in the Computing Divsion at Fermilab. The OSG DocDB web address is osg-docdb.opensciencegrid.org.

## Owners
This SLA is owned by OSG Communications and Fermilab and will be reviewed and agreed upon by the OSG Executive Team and OSG Stakeholders.

## Service Name and Description
### Name
OSG Document Repository (DocDB)

### Description

OSG DocDB is a document repository used for public documentation related to work in the OSG, including blueprint documents, presentations given at a conference or collaboration meeting or papers published in a journal, among others.

## Security Considerations

Accessibility to documents in the repository is at the document version level. Some documents are viewable to the public, others are not. Write access is based on a user's membership in DocDB security groups. Each DocDB user must use either their IGTF, DOEGrids, or Fermilab KCA certificate in order to access private content or to create or update documents. Based on their role within the organization, they are given membership to the applicable groups. All group membership requires approval by an OSG Council member or by a member of OSG management.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The OSG DocDB is a 9 x 5 service. | The issue causes a full service outage rendering the OSG DocDB unavailable | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all OSG DocDB users | The issue may or may not affect all users | The issue affects only a small number of users |
| *Response Time* | * * | * * | * * |
| N/A | Within the next business day | Within the next business day | Within five (5) business days |
| *Resolution Time* | * * | * * | * * |
| N/A | The maximum acceptable resolution time is one full (1) business day | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is thirty (30) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | One Day | One Week | One Month |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG DocDB Administrator |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and [Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages

Planned outages will be announced in advance via the GOC. OSG Communications will strive for 97% service availability. If service availability falls below 97% monthly as monitored by OSG Communications on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The software service is supported 9x5 M-F by the OSG Communications activity and the Fermilab Computing Division. All issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All software issues should be reported to the GOC by [trouble ticket](https://ticket.grid.iu.edu/goc/twiki) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on the Fermilab Computing Division's determination of the necessity and desirability of the enhancement. The Fermilab Computing Division reserves the right to enhance the physical environment of the service based on Fermilab needs. No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
DocDB service problems should be reported by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/twiki (*preferred*)
   * Calling the GOC phone at 317-275-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
OSG DocDB customers agree to:

   * Use the OSG DocDB service for purposes of VO or OSG approved work only.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.

<a name="OSG_Communications_Responsibilities"></a>
### OSG Communications Responsibilities
General responsibilities:
   * Application administration
   * User support and requests (First point of contact. Server issues will be directed to Fermilab Computing Division/Web, Unified Communications & Collaboration Services group.)
   * Create and add appropriate documentation to the OSG DocDB home page for appropriate use of OSG DocDB.
   * Meet response times associated with the priority assigned to Customer issues.

### Fermilab Computing Division/Web, Unified Communications & Collaboration Services group Responsibilities:
   * Maintaining the hardware of the host DocDB machine, www-docdb.fnal.gov
   * Maintaining the Apache server, including patching, updates, and server configuration.
   * Ensuring full backups of the service on a monthly basis.
   * Keeping backup data for a period of one year.
   * Meet response times associated with the priority assigned to Customer issues.

### GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.
   * Alert the community of maintenance/upgrades/outages as reported by OSG Communications.


## Service Measuring and Reporting
OSG Communications will provide the customer with reports regarding Service Uptime and Report of Critical and High Priority Issues as requested:


These reports will be posted in Appendix E of this document.

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Communications Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All OSG Document Repository service end-users who are members of an OSG VO and OSG staff members are considered customers.

# Appendix B - Other Service Dependencies
The OSG Document Repository service is dependent on the following services:

   * Fermilab Networking, IGTF certificate software.

## Software Services
Service Provider agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Communications Responsibilities](#osg-communications-responsibilities) section of this document.


# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| | | |

# Appendix E - Metric Reports


