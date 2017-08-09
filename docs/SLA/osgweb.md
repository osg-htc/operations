# OSG Web Portal Service Level Agreement -- *DRAFT*

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.0 | 6-04-2010 | Marcia Teckenbrock | First Draft |



## Executive Summary
This SLA is an agreement between the Service Providers: Tilted Planet Ltd and XenoMedia, and the Customers: OSG Management, OSG Communications and the OSG Stakeholders. It describes details of the OSG web portal service. The OSG web portal is used for public information about the OSG. The www.opensciencegrid.org domain is owned by Open Science Grid and hosted by Tilted Planet, Ltd. OSG Communications is responsible for maintaining and updating the web content. Xeno Media provides technical support for the content management system software that underlies the web site.

## Owners
This SLA is owned by OSG Communications and Fermilab and will be reviewed and agreed upon by the OSG Executive Team and OSG Stakeholders.

## Service Name and Description
### Name
OSG Web Portal

### Description

The OSG web portal is used for public information relating to the OSG project. It is meant to be the main method of conveying new or prospective users to other areas, including the Twiki (for technical information) and the document respository.

## Security Considerations

All information on www.opensciencegrid.org is publicly viewable.

On the server-side, the site has a full system account for access control.

The web application has access control in that all content changes are tagged and versioned with the username of the editor. All content changes can be reverted at-will.


## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancement) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The OSG web portal is a 24 x 7 service. | The issue causes a full service outage rendering the OSG web portal unavailable | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all OSG web portal users | The issue may or may not affect all users | The issue affects only a small number of users |
| *Response Time* | * * | * * | * * |
| N/A | Within the next business day | Within the next business day | Within five (5) business days |
| *Resolution Time* | * * | * * | * * |
| N/A | The maximum acceptable resolution time is one full (1) business day | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is thirty (30) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | One Day | One Week | One Month |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | webmaster@opensciencegrid.org, support@tilted.com |
| 2nd | 911@tilted.com, 866-484-5833 |
| 3rd | |
| 4th | |

Any ongoing "High" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/blob/master/SLA/ProductionMeetingMinutes) and

## Service Availability and Outages

Planned outages will be announced to customers in advance. The Service Providers will strive for 97% service availability. If service availability falls below 97% monthly as monitored by OSG Communications on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The software service is supported 9x5 by Xeno Media. All matters will be investigated by the next business day. The hardware service is supported 24x7 by Tilted Planet Ltd via phone and email helpdesk.

## Service Off-Hours Support Procedures
All software issues should be reported to the GOC by [trouble ticket](https://ticket.grid.iu.edu/goc/twiki) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-prioriti) for information on unplanned outages.

The Service Providers will respond to customer requests for service enhancements based on the Fermilab Computing Division's determination of the necessity and desirability of the enhancement. The Fermilab Computing Division reserves the right to enhance the physical environment of the service based on Fermilab needs. No enhancement will occur without advanced notice to the OSG Executive Team.

## Customer Problem Reporting
OSG Web Portal service problems should be reported by one of the following mechanisms.

   * Xeno Media Content Management System: [insert reporting method here].
   * Web Server support: Tilted Planet Ltd phone or email helpdesk system [insert # and address here].
   *

## Responsibilities
### Customer Responsibilities
OSG Web Portal customers agree to:

   * Use the OSG Web Portal service for purposes of VO or OSG approved work only.
   * Contact the Service Providers by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.

<a name="OSG_Communications_Responsibilities"></a>

### Tilted Planet Ltd Responsibilities
General responsibilities:
   * Make daily tape backups that are stored away from the web servers.
   * Meet response times associated with the priority assigned to Customer issues.
   * Alert the community of maintenance/upgrades/outages.

### Xeno Media Responsibilities
General responsibilities:
   * .Meet response times associated with the priority assigned to Customer issues.


### OSG Communications Responsibilities
General responsibilities:
   * Create and maintain appropriate information on the OSG web portal.


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
All OSG DocDB service end-users who are members of an OSG VO and OSG staff members are considered customers.

# Appendix B - Other Service Dependencies
The OSG DocDB service is dependent on the following services:

   * Backup. Service Provider agrees to fully back up all Service Provider-supported software and data nightly every business day.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| | | |

# Appendix E - Metric Reports

   * [](http://www.opensciencegrid.org/webstats/)Web Metrics
   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]
