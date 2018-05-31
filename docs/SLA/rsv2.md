# OSG RSV Collection and Distribution Service, Version 2. Service Level Agreement

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 3-7-2018 | Scott Teige | Intital document |

## Executive Summary
This SLA is an agreement between OSG Operations at Indiana University and the OSG Management describing details of 
a replacement for the OSG Resource and Service Validation (RSV) central collection and distribution.
The RSV Collector service runs on hardware at Indiana University and provides collection and distribution of RSV records.

## Owners
This SLA is owned by OSG Operations Center and Indiana University and will be reviewed and agreed upon
by the OSG Executive Team.

## Service Name and Description
### Name
GOC Production RSV2 Collector

### Description

The original GOC RSV Collector received RSV records from local OSG Resources and 
distributed records to several reporting services including but not limited to MyOSG and WLCG SAM.

This service determines status information of Compute Elements, Stash Cache Servers and HTCondor collectors.
The availability of theses resources for the periods of 24 hours, 7 days and 30 days is calculated and presented.

## Security Considerations
All information collected and distributed is public. 
The RSV Collector uses the Condor Collector operated by the GOC at Indiana University as the source of information.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The RSV2 Collector does not have critical priority | The issue causes a full service outage rendering RSV records unavailable for collection or distribution | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| N/A | The issue affects all RSV2 Collector users | The issue may or may not affect all users | The issue affects only a small number of users |
| *Response Time* | * * | * * | * * |
| N/A | Within the next business day | Within the next business day | Within the next business day |
| *Resolution Time* | * * | * * | * * |
| N/A | The maximum acceptable resolution time is 24 continuous hours, after the initial response time | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is thirty (30) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | One Day | One Week | One Month |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Detailed information on contacts are viewable on the following 
[MyOSG URL](https://my.opensciencegrid.org/rgsummary/xml?datasource=summary&summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&gip_status_attrs_showfqdn=on&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&start_type=7daysago&start_date=09/15/2009&end_type=now&end_date=09/15/2009&site_10047=on&rg=on&rg_246=on&gridtype=on&gridtype_1=on&voown=on&voown_25=on&active=on&active_value=1&disable_value=1),

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and [Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages
The GOC will strive for 97% service availability.
If service availability falls below 97% monthly as monitored by the GOC on two consecutive
months a root cause analysis and service plan will be submitted to the OSG stakeholders for
plans to restore an acceptable level of service availability.

## Service Support Hours
The software service is supported 24x7 by the GOC and Indiana University.
High level issues will result in response within (1) day.
All other issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All software issues should be reported to the GOC immediately by
[trouble ticket](https://ticket.grid.iu.edu/goc/software) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages.
Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times)
for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC 
determination of the necessity and desirability of the enhancement. The GOC reserves the right to 
enhance the physical environment of the service based on IU and GOC needs.
No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
The GOC provides operators 24x7x365. 
RSV Collector problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
OSG RSV Collector customers agree to:

   * Use the OSG RSV2 Collector for purposes of VO or OSG approved work only.
   * Alert the GOC if they are going to use the RSV2 Collector in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide information within one business day for any High level issues reported.
   * Provide testing for the OSG RSV2 Collector within the time frame defined in the [Requests for Service Enhancements](#requests-for-service-enhancements) section.
   * Alert the GOC when problems are encountered during testing.

### OSG Operations Responsibilities
General responsibilities:
   * Meet response times associated with the priority assigned to Customer issues.
   * Maintain appropriately trained staff.
   * The OSG and GOC are not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.
   * Make changes and updates within the normal GOC [release schedule](https://github.com/opensciencegrid/operations/blob/master/docs/agile_maintenance.md)

GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.


## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All OSG RSV2 Collector end-users who are members of an OSG VO are considered customers.

# Appendix B - Other Service Dependencies
The OSG RSV Collector is dependent on the following services to collect and distribute information:
   * Local Network, Hardware, OS, Condor Collectors

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
Service Provider agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Operations Responsibilities](https://github.com/opensciencegrid/operations/blob/master/SLA/RSVServiceLevelAgreement#osg-operations-responsibilities) section of this document.

## Software Costs
IU and the Grid Operations Center bears all costs for new and replacement software.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| | | |

