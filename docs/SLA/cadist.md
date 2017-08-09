
# OSG Certificate Authority Distribution and Software Cache Service Level Agreement

## About This Document
This document details a service level agreement which outlines production expectations for the OSG software cache and defines general support infrastructure for the service.

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 9-15-2009 | Rob Quick | First Draft |
| 1.2 | 2-9-2010 | Rob Quick | Revised |


## Executive Summary
This SLA is an agreement between OSG Operations at Indiana University and the OSG Management describing details of the OSG Certificate Authority (CA) Distribution and OSG Software Cache. The CA Distribution and Software cache service runs on hardware at Indiana University and provides access to latest the OSG CA distribution and OSG Production and ITB software caches.

## Owners
This SLA is owned by OSG Operations Center and Indiana University and will be reviewed and agreed upon by the OSG Executive Team.

## Service Name and Description
### Name
GOC Production Software Cache

### Description
The GOC Production Software cache hold files necessary to update the OSG CA distribution and current OSG Production and ITB Middleware stacks.

## Security Considerations
Since the software cache distributes the IGTF CA information, a non-IGTF commercial certificate is used on this machine. All caches are read only by web access, and only GOC staff has access to change of modify the Software Cache.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancement) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The software cache does not have critical priority | The issue causes a full service outage rendering the cache unavailable for access | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all software cache users | The issue may or may not affect all software cache users | The issue affects only a small number of software cache users |
| *Response Time* | * * | * * | * * |
| N/A | Within the next business day | Within the next business day | Within the next business day |
| *Resolution Time* | * * | * * | * * |
| N/A | The maximum acceptable resolution time is 24 continuous hours, after the initial response time | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is (30) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | One Day | One Week | One Month |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Detailed information on contacts are viewable on the following [Software Cache Contacts URL](https://myosg.grid.iu.edu/rgsummary/index?datasource=summary&summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&downtime_attrs_showpast=&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&bdiitree_type=total_jobs&bdii_object=service&bdii_server=is-osg&start_type=7daysago&start_date=09%2F15%2F2009&end_type=now&end_date=09%2F15%2F2009&site_10047=on&rg=on&rg_270=on&gridtype=on&gridtype_1=on&service_central_value=0&service_hidden_value=0&voown=on&voown_25=on&active=on&active_value=1&disable_value=1), and are maintained within the

Any ongoing "High" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/blob/master/SLA/ProductionMeetingMinutes) and

## Service Availability and Outages
The GOC will strive for 97% service availability. If service availability falls below 97% monthly as monitored by the GOC on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The software service is supported 24x7 by the GOC and Indiana University. High level issues will result in response within (1) day. All other issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All software issues should be reported to the GOC immediately by [trouble ticket](http://ticket.grid.iu.edu) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-prioriti) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC determination of the necessity and desirability of the enhancement. The GOC reserves the right to enhance the physical environment of the service based on IU and GOC needs. No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
The GOC provides operators 24x7x365. Software cache problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/software (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
OSG Software Cache Customers agree to:

   * Use the OSG Software Cache for purposes of VO approved work only.
   * Alert the GOC if they are going to use the Software Cache in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](https://github.com/opensciencegrid/operations/blob/master/SLA/ServiceCacheServiceLevelAgreement#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide information within one business day for any High level issues reported.
   * Provide testing for the OSG Software Cache within the time frame defined in the [Requests for Service Enhancements](https://github.com/opensciencegrid/operations/blob/master/SLA/SoftwareCacheServiceLevelAgreement#requests-for-service-enhancement) section.
   * Alert the GOC when problems are encountered during testing.

### OSG Operations Responsibilities
General responsibilities:
   * Create and add appropriate documentation to the OSG TWiki for appropriate use of the OSG Software Cache.
   * Meet response times associated with the priority assigned to Customer issues.
   * Maintain appropriately trained staff.
   * The OSG and GOC are not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.
   * Make changes and updates within the normal GOC release schedule documented at https://github.com/opensciencegrid/operations/blob/master/SLA/ReleaseSchedule.

GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.

Database & Application Services responsibilities:
   * Announce and negotiate maintenance with stakeholders to assure minimal interruption to normal workload.
   * Alert the community of scheduled maintenance periods at least three (3) business days prior to the start of a service affecting maintenance window.

## Service Measuring and Reporting
The GOC will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Uptime | Monthly | Web Posting | GOC |
| Service Uptime | Monthly | Web Posting | GOC |
| Report of Critical and High Priority Issues | Quarterly | Web Posting | GOC |

These will be included in Appendix E of this document.

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All OSG Software Cache end-users who are members of an OSG VO are considered customers.

# Appendix B - Other Service Dependencies
The OSG Software Cache is dependent on the following services to serve cache information:
   * Local Network, Hardware, OS, and Apache

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
Service Provider agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Operations Responsibilities](https://github.com/opensciencegrid/operations/blob/master/SLA/SoftwareCacheServiceLevelAgreement#osg-operations-responsibilities) section of this document.

## Software Costs
IU and the Grid Operations Center bears all costs for new and replacement software.

# Appendix D - Approval
| Approved By | Position | Date |
| ----------- | -------- | ---- |
| | | |

# Appendix E - Metric Reports
   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]

