# Glide-In Factory Service Level Agreement

## About This Document
This document details a service level agreement which outlines production expectations for GlideInWMS and defines general support infrastructure for the service.

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 8-19-2010 | Igor Sfiligoi | First Draft |
| 1.2 | 10-4-2010 | Rob Quick | First Draft (TWiki Form)|
| 1.3 | 10-8-2010 | Igor Sfiligoi, Rob Quick | Second Draft |
| 1.4 | 10-20-2010 | Rob Quick | Removed from Draft Status |


## Executive Summary
This SLA is an agreement between OSG and OSG Stakeholders pertaining to the operation of the OSG GlideInWMS factory instance. A GlideInWMS factory will be run at UCSD, IU and CERN and provide an integral service of the GlideInWMS system to OSG Stakeholders.

## Owners
The GlideInWMS SLA is owned by OSG Operations. It will be reviewed by and agreed upon by the OSG Executive Team.

## Service Name and Description
### Name
OSG GlideInWMS Factory


### Description
The grid-facing component of the GlideInWMS service available for use by all OSG VOs. The "factory" submits pilot jobs through the grid at all sites a VO specifies. This factory removes the need for the VO to directly interact with the OSG's CE service.

## Security Considerations
The VO delegates its proxy to the GlideInWMS factory in order for the factory to submit jobs as the VO itself. This means any critical security incident at the GlideInWMS factory intimately affects the operations of the VO itself.

The GlideInWMS factory service operators are free to share configurations or debugging information from the VO on non-public lists and emails, even if it contains personally identifiable information about the VO's users. If the information is to be presented in a public forum, the GlideInWMS factory service operators need prior permission from the OSG Stakeholders using the WMS Glide-In Factory.

The GlideinWMS factory service operators are free to share summary and/or anonymous data in public forum.


## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Description* | * * | * * | * * |
| The issue can cause a likely security incident | The issue prevents any new slots from joining the Condor pool | The issue causes the pilots death or instability at some sites, reducing the ability of the Condor pool to do science | The issue prevents effective monitoring or full utilization of the Condor pool |
| *Response Time* | * * | * * | * * |
| Within 4 business hours or within 24 hours, whatever is shorter | Within 4 business hours | Within 2 business days | Within 10 business days |
| *Resolution Time* | * * | * * | * * |
| Containment within 24 hours. Remediation within 1 business day. | Within One Business Day | The maximum acceptable resolution time is five (5) business days | The maximum acceptable resolution time is ten (10) business days |
| *Escalates Every* | * * | * * | * * |
| One Day | Two Days | Five Days | Ten Days |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Critical Level Security Issues will be elevated immediately to the OSG Security Team.

Detailed information on contacts are viewable on the following [MyOSG URL](https://myosg.grid.iu.edu/rgsummary/index?datasource=summary&summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&gip_status_attrs_showfqdn=on&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&start_type=7daysago&start_date=09/15/2009&end_type=now&end_date=09/15/2009&site_10047=on&rg=on&rg_246=on&gridtype=on&gridtype_1=on&voown=on&voown_25=on&active=on&active_value=1&disable_value=1), and are maintained within the

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and [Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages
The GOC will strive for 90% service availability. If service availability falls below 90% monthly as monitored by the GOC a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

Reliability and availability will be determined by 2 critical RSV probes and the OSG availability algorithm.
   * One probe will verify the Condor collector is queryable whenever the host is pingable (i.e., reasonably not a network failure).
   * The other probe will verify pilots are being submitted to the OSG within 30 minutes of their request.
All outages will be logged at least in the OSG ticketing system.

## Service Support Hours
This service will be run for 24x7, but support will primarily be within business hours. The exception is for security incidents.

## Service Off-Hours Support Procedures
All operational issues should be reported as per [Customer Problem Reporting](#customer-problem-reporting) section.

## Requests for Service Enhancements
OSG Operations will provide enhancement capabilities only as they are released by the GlideInWMS project. Requests for customization of the deployed service may be made; OSG Operations has the right of up to one month of testing of any change.

OSG will give 1 week of warning prior to any change in the GlideInWMS service version. At any time during this week, Stakeholders are permitted to request a delay for up to 1 week after the originally scheduled upgrade.

   * The exception is for code changes that are deemed critical by the GlideinWMS Factory operations staff. A critical change can be put into place after 72 hours of warning or immediately if approved by affected stakeholders. Afterward, OSG Operations will provide a written report detailing the critical change that was made and an analysis of how it will be avoided in the future.
   * Immediately exploitable security-related code fixes can further reduce the above time window to 24 hours.
   * Furthermore, minor code changes that do not affect the semantics of the operations are exempt from the notification requirements.

OSG Operations will schedule downtimes and configuration changes during normal business hours unless approved by affected stakeholders. This is done so affected stakeholders are always on-hand in case if the downtime and changes cause further issues.


## Customer Problem Reporting
The GOC provides operators 24x7x365. GlideinWMS Factory related problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/open (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org


## Responsibilities

   * A GlideInWMS Factory will be run by OSG Operations and accessible to the GlideInWMS VO frontend.
   * The Condor pool served by the GlideInWMS Factory will have the ability to scale up to 10,000 running jobs and 100,000 waiting jobs. In order to do achieve this, the GlideInWMS Factory operators expects stakeholders to have the following hardware:
   * For running 1000 jobs, provide a single node with at least two reasonably recent cores and 8GB of memory. Disk space as needed to host the user files.
   * For 5000 jobs, provide two nodes, one like above to be used for running the schedd, plus another one with at least two modern cores and 4 GB of memory to run the collectors and frontend.
   * For 10000 jobs, provide two nodes, one with 2 cores and 16GB of memory for the schedd, and another with 2 cores and 8 GB of memory for the collectors and frontend.
   * OSG Operations will be responsible for debugging pilot submission issues at OSG sites. They will be responsible for debugging issues developed by the pilot infrastructure. Their responsibility ends when the job is successfully launched by Condor.
   * OSG Operations will provide best effort assistance for issues pertaining to the VO frontend. The GlideInWMS project, not OSG, is responsible for software bugs.
   * The GlideinWMS Factory operators will not submit jobs to sites that have not been validated by the VO running the jobs.. In the initial period, the stakeholder is expected to provide the list of validated sites to the GlideinWMS Factory operators. If at one point in time the stakeholder provides validation criteria the GlideinWMS Factory operators can implement, the operators themselves will take over the task of discovering and validating new OSG sites to run pilot jobs on.
   * Affected stakeholders are expected to perform logging and accounting of all jobs run in the previous 30 days for security purposes.


## Service Measuring and Reporting
The GOC will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Availability and Reliability | Monthly | Web Posting | GOC |
| Report of Critical and High Priority Issues | Quarterly | Web Posting | OSG Operations |
| Summary of Changes | Quarterly | Web Posting | OSG Operations |

These will be included in Appendix B of this document.

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Approval
| Approved By | Position | Date |
| ----------- | -------- | ---- |
| | | |

# Appendix B - Metric Reports
   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]

# Appendix C - VOs Using Glide-In WMS

   * HCC
   * USCMS
   * NEBioGrid
   * GLOW
   * GlueX
   * IceCube
