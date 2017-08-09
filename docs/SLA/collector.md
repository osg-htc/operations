
# GOC Condor Collector Service Level Agreement

## About This Document
This document details a service level agreement which outlines production expectations for the GOC Condor Collector and defines general support infrastructure for the service.

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 9-24-2014 | Scott Teige | First Draft |


## Executive Summary
This SLA is an agreement between OSG and OSG Stakeholders pertaining to the operation of the OSG Condor Collector service.

## Owners
The Condor Collector SLA is owned by OSG Operations. It will be reviewed by and agreed upon by the OSG Executive Team.

## Service Name and Description
### Name
GOC Condor Collector


### Description
The grid-facing component of the HTCondor compute element system available for use by all OSG VOs.

## Security Considerations
All information associated with the service is covered by the Indiana University [privacy policy](https://github.com/opensciencegrid/operations/blob/master/SLA/IUPrivacyPolicy).
Effect of compromise of this service are limited to the service. A compromise may make the service unusable by compute elements using it.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Description* | * * | * * | * * |
| This service does not have critical priority | This service does not have high priority | This issue prevents all new sites from advertising in the info service or clients from querying the service. This issue causes intermittent drops of updates or query failures. | The issue prevents effective monitoring or full utilization of the Condor pool |
| *Response Time* | * * | * * | * * |
| N/A | N/A | Within 2 business days | Within 10 business days |
| *Resolution Time* | * * | * * | * * |
| N/A | N/A | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is ten (10) business days |
| *Escalates Every* | * * | * * | * * |
| N/A | N/A | Five Days | Ten Days |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Critical Level Security Issues will be elevated immediately to the OSG Security Team.

Detailed information on contacts are viewable on the following [MyOSG URL](https://myosg.grid.iu.edu/rgsummary/index?datasource=summary&summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&gip_status_attrs_showfqdn=on&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&start_type=7daysago&start_date=09/15/2009&end_type=now&end_date=09/15/2009&site_10047=on&rg=on&rg_246=on&gridtype=on&gridtype_1=on&voown=on&voown_25=on&active=on&active_value=1&disable_value=1), and are maintained within the

Any ongoing "High" or "Elevated" level issues will be discussed at the weekly Operations and Production meetings.

## Service Availability and Outages
The GOC will strive for 90% service availability. If service availability falls below 90% monthly as monitored by the GOC a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

Reliability and availability will be determined by 2 critical RSV probes and the OSG availability algorithm.
   * One probe will verify the Condor collector is queryable whenever the host is pingable (i.e., reasonably not a network failure).
   * The other probe will verify an automatically generated configuration file has been updated recently

## Service Support Hours
This service will be run for 24x7, but support will primarily be within business hours. The exception is for security incidents.

## Service Off-Hours Support Procedures
All operational issues should be reported as per [Customer Problem Reporting](#customer-problem-reporting) section.

## Requests for Service Enhancements
OSG Operations will provide enhancement capabilities only as they are released by the HTCondor project or OSG Technology Group.
Requests for customization of the deployed service may be made; OSG Operations has the right of up to one month of testing of any change.

OSG will give 1 week of warning prior to any change in the Collector service version.
At any time during this week, Stakeholders are permitted to request a delay for up to 1 week after the originally scheduled upgrade.

OSG Operations will schedule downtimes and configuration changes during normal business hours unless approved by affected stakeholders. This is done so affected stakeholders are always on-hand in case if the downtime and changes cause further issues.


## Customer Problem Reporting
The GOC provides operators 24x7x365. Problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/open (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org


## Responsibilities

   * The Collector will be run by OSG Operations and accessible to HTCondor compute elements.
   * Problems not associated with the hardware, operating system or network are the responsibilty of the Technology Group.

## Service Measuring and Reporting
The GOC will provide the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Availability and Reliability | Monthly | Web Posting | GOC |

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Approval
| Approved By | Position | Date |
| ----------- | -------- | ---- |
| | | |


<-- CONTENT MANAGEMENT PROJECT
############################################################################################################
DEAR DOCUMENT OWNER
===================

Thank you for claiming ownership for this document Please fill in your FirstLast name here:
   * Local OWNER = RobQ

Please define the document area, choose one of the defined areas from the next line
DOC_AREA = (ComputeElement|General|Trash/Trash/Integration|Monitoring|Operations|Security|Storage|Trash/Tier3|User|VO)
   * Local DOC_AREA = Operations

define the primary role the document serves, choose one of the defined roles from the next line
DOC_ROLE = (Developer|Documenter|Scientist|Student|SysAdmin|VOManager)
   * Local DOC_ROLE = VOManager

Please define the document type, choose one of the defined types from the next line
DOC_TYPE = (HowTo|Installation|Knowledge|Navigation|Planning|Training|Troubleshooting)
   * Local DOC_TYPE = Knowledge

Please define if this document in general needs to be reviewed before release ( %YES% | %NO% )
   * Local INCLUDE_REVIEW = %YES%

Please define if this document in general needs to be tested before release ( %YES% | %NO% )
   * Local INCLUDE_TEST = %NO%

change to %YES% once the document is ready to be reviewed and back to %NO% if that is not the case
   * Local REVIEW_READY = %YES%

change to %YES% once the document is ready to be tested and back to %NO% if that is not the case
   * Local TEST_READY = %NO%

change to %YES% only if the document has passed the review and the test (if applicable) and is ready for release
   * Local RELEASE_READY = %NO%


DEAR DOCUMENT REVIEWER
======================

Thank for reviewing this document Please fill in your FirstLast name here:
   * Local REVIEWER = ScottTeige

Please define the review status for this document to be in progress ( %IN_PROGRESS% ), failed ( %NO% ) or passed ( %YES% )
   * Local REVIEW_PASSED = %YES%


DEAR DOCUMENT TESTER
====================

Thank for testing this document Please fill in your FirstLast name here:
   * Local TESTER = ScottTeige

Please define the test status for this document to be in progress ( %IN_PROGRESS% ), failed ( %NO% ) or passed ( %YES% )
   * Local TEST_PASSED = %IN_PROGRESS%
############################################################################################################
-->

