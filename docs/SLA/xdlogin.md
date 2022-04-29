# XD-Login Service Level Agreement

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 0.1 | 2-18-2013 | Scott Teige | First Draft |



## Executive Summary
This SLA is an agreement between OSG Operations, Information Sciences Institute (ISI) and the OSG Management and Stakeholders describing details
of the OSG-XD job submission system.

## Owners
This SLA is owned by OSG Operations, Indiana University and ISI and will be reviewed and agreed upon by the OSG Executive Team and OSG Stakeholders.

## Service Name and Description
### Name
The service is built on two physical machines hosted by the GOC. These are
the production XD-Login job submission node and an adjunct machine, OSG-FLOCK.

### Description

The XD-Login submission node allows OSG resources to be accessed by XSEDE users. A complete description is available [here.](https://www.xsede.org/OSG-User-Guide)

## Security Considerations

The XD-Login submission node supports Single Sign On through the XSEDE User Portal, and also from the command line using gsissh with a grid certificate for authentication.
OSG-FLOCK is not publicly accesible.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| This Service does not have critical priority | The issue causes a full service outage rendering the service unavailable | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all users | The issue may or may not affect all users | The issue affects only a small number of users |
| *Response Time* | * * | * * | * * |
| N/A | Within the next business day | Within the next business day | Within five (5) business days |
| *Resolution Time* | * * | * * | * * |
| N/A | The maximum acceptable resolution time is one full (1) business day | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is thirty (30) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | One Day | One Week | One Month |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Detailed information on contacts are viewable on the following [MyOSG URL](https://my.opensciencegrid.org/rgsummary/xml?summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&downtime_attrs_showpast=&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&bdiitree_type=total_jobs&bdii_object=service&bdii_server=is-osg&start_type=7daysago&start_date=09%2F15%2F2009&end_type=now&end_date=09%2F15%2F2009&site_10047=on&rg=on&rg_336=on&gridtype=on&gridtype_1=on&active=on&active_value=1&disable_value=1), and are maintained within the

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](/#weekly-operations-meetings) and [Production](https://osg-htc.org/production/#weekly-production-meetings)) meetings.

## Service Availability and Outages

The GOC will strive for 97% service availability. If service availability falls below 97% monthly as monitored by the GOC on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The service is supported 24x7 by the GOC and Indiana University. All issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
XSEDE users should report problems via the [XSEDE trouble ticket](https://portal.xsede.org/help-desk) system. Others should contact the GOC via the

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC determination of the necessity and desirability of the enhancement. The GOC reserves the right to enhance the physical environment of the service based on IU and GOC needs. No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
The GOC provides operators 24x7x365. Service problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://tickets.xsede.org (*preferred for XSEDE users*)
   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/submit (*preferred for other users*)
   * Emailing a description to XD-Login-support@opensciencegrid.org
   * Calling the GOC phone at 317-278-9699

## Responsibilities
### Customer Responsibilities
XD-Login customers agree to:

   * Use the service for purposes of XSEDE or OSG approved work only.
   * Alert the GOC if they are going to use the Service in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact support by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide information within one business day for any High level issues reported.


### OSG Operations Responsibilities

GOC operations:
   * Maintain the physical machine hosting the service
   * Assure the service is accessible via its advertised URL
   * Make changes and updates within the normal GOC release schedule
   * Meet response times associated with the priority assigned by users for issues related to the hardware.
   * Maintain appropriately trained staff.
   * The OSG and GOC are not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.

ISI:
   * Is responsible for all aspects of the service not listed above.

GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.

Database & Application Services responsibilities:
   * Announce and negotiate maintenance with stakeholders to assure minimal interruption to normal workload.
   * Alert the community of scheduled maintenance periods at least five (5) business days prior to the start of a service affecting maintenance window.

## Service Measuring and Reporting
The GOC will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Uptime | Monthly | Web Posting | GOC |
| Service Uptime | Monthly | Web Posting | GOC |
| Report of Critical and High Priority Issues | Quarterly | Web Posting | GOC |

These reports will be posted in Appendix E of this document.

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, a representitive of ISI, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All service end-users who are members of an OSG VO and OSG Staff are considered customers.
All XSEDE staff and all XSEDE users with an OSG allocation are also customers.

# Appendix B - Other Service Dependencies
The service is dependent on the following services to collect and distribute information:
   * Local Network and Hardware

# Appendix C - Supported Hardware and Software

## Supported Hardware
The following hardware is supported:
   * Physical devices used to provide the service.
   * Physical devices used to provide the environment used to house the service.

## Hardware Services
The following hardware services are provided:
   * Recommendations. OSG Operations will be responsible for specifying and recommending for purchase or lease hardware meeting customers' needs.
   * Installation. OSG Operations will install, configure and customize system hardware and operating systems.
   * Upgrades. OSG Operations is responsible for specifying and recommending for purchase any hardware upgrades.
   * Diagnosis. OSG Operations will diagnose problems with service related hardware.
   * Repair. OSG Operations analysts are not hardware technicians and receive no training in hardware maintenance, nor do we have the test equipment and tools necessary to do such work.

Performing repairs under warranty: Any work to be performed under warranty may be referred to the warranty service provider at the discretion of the Service Provider analyst(s). Service Provider analysts will not undertake work that will void warranties on customer hardware unless specifically requested and authorized by customer's management in writing.

Obtaining repair services: The Service Provider analyst will recommend a service vendor whenever he/she feels the repair work requires specialized skills or tools.

   * Backup. Service Provider agrees to fully back up all Service Provider-supported software and data nightly every business day.

## Software Services
Service Provider agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Operations Responsibilities](#osg-operations-responsibilities) section of this document.

## Software Costs

IU and the Grid Operations Center bears all costs for new and replacement software.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| | | |

# Appendix E - Metric Reports
   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]

