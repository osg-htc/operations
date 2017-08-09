-- Main.ScottTeige - 23 Jan 2012
# OSG JIRA Service Level Agreement

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 1-23-2012 | Scott Teige | First Draft |
| 1.2 | 2-7-2012 | Rob Quick | Revision and Approval |



## Executive Summary
This SLA is an agreement between OSG Operations and the OSG Management and Stakeholders describing details of the OSG JIRA Service. The OSG JIRA is used by OSG staff for software and administrative project tracking. The OSG JIRA service runs on hardware at Indiana University. The web address is jira.grid.iu.edu.

## Owners
This SLA is owned by OSG Operations and Indiana University and will be reviewed and agreed upon by the OSG Executive Team and OSG Stakeholders.

## Service Name and Description
### Name
Production OSG JIRA

### Description

JIRA provides a project tracking system for use by OSG staff. Predefined projects exist and tickets are created within a project.

## Security Considerations

Access to JIRA is restricted to registered users. A username/password login is required. New users are added by the JIRA administrators. Additionally, individual projects can restrict access to specific subsets of users.

Use of the information contained in the system is governed by the Indiana University [privacy policy.](https://github.com/opensciencegrid/operations/blob/master/SLA/IUPrivacyPolicy)

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The OSG JIRA Service does not have critical priority | The issue causes a full service outage rendering the OSG JIRA unavailable | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all OSG JIRA users | The issue may or may not affect all users | The issue affects only a small number of users |
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

Any ongoing "High" or "Elevated" level issues will be discussed at the weekly Operations and Production meetings.

## Service Availability and Outages

OSG Operations will strive for 97% service availability. If service availability falls below 97% monthly as monitored by OSG Operations on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The service is supported 24x7 by the GOC and Indiana University. All issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All issues should be reported to the GOC immediately by [trouble ticket](https://ticket.grid.iu.edu/goc/custom) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC determination of the necessity and desirability of the enhancement. OSG Operations reserves the right to enhance the physical environment of the service based on IU and OSG Operations needs. No enhancement will occur without advanced notice to OSG staff

## Customer Problem Reporting
The GOC provides operators 24x7x365. JIRA service problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket [here](https://ticket.grid.iu.edu/goc/custom) (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
OSG JIRA customers agree to:

   * Use the OSG JIRA service for purposes of VO or OSG approved work only.
   * Alert the GOC if they are going to use the OSG JIRA Service in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide information within one business day for any High level issues reported.
   * Provide testing for the OSG JIRA service within the time frame defined in the [Requests for Service Enhancements](#requests-for-service-enhancements) section.
   * Alert the GOC when problems are encountered during testing.

### OSG Operations Responsibilities
General responsibilities:
   * Meet response times associated with the priority assigned to Customer issues.
   * Maintain appropriately trained staff.
   * The OSG Operations is not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.
   * Make changes and updates within the normal GOC [release schedule](https://github.com/opensciencegrid/operations/tree/master/docs/SLA/ReleaseSchedule.md)
GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.

Database & Application Services responsibilities:
   * Announce and negotiate maintenance with stakeholders to assure minimal interruption to normal workload.
   * Alert the community of scheduled maintenance periods at least five (5) business days prior to the start of a service affecting maintenance window.

## Service Measuring and Reporting
OSG Operations will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Uptime | Monthly | Web Posting | GOC |
| Service Uptime | Monthly | Web Posting | GOC |
| Report of Critical and High Priority Issues | Quarterly | Web Posting | GOC |

These reports will be posted in Appendix E of this document.

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All OSG JIRA service users or OSG Staff are considered customers.

# Appendix B - Other Service Dependencies
The JIRA service is dependent on the following services to collect and distribute information:
   * Local Network, Hardware, OS, JIRA Software, and Apache

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

IU and OSG Operations bear all costs for new and replacement software.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| Rob Quick | OSG Operations Coordinator | 2-7-2012 |

# Appendix E - Metric Reports
   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]

### Comments


