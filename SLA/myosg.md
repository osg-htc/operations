# MyOSG Service Level Agreement



## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| [1.1](https://github.com/opensciencegrid/operations/blob/master/SLA/myosg.md?rev=2) | 5-26-2009 | Rob Quick | First Draft |
| [1.2](https://github.com/opensciencegrid/operations/blob/master/SLA/myosg.md?rev=7) | 9-10-2009 | Rob Quick | Second Draft |
| 1.3 | 9-15-2009 | Rob Quick | Final Draft, Ready for Circulation |
| 1.4 | 11-30-2009 | Rob Quick | FNAL Updates |

## Executive Summary
This SLA is an agreement between OSG Operations at Indiana University and the OSG Management describing details of the MyOSG presentation tools. The MyOSG service runs on hardware at Indiana University and gathers data from several OSG sources including but not limited to: RSV, OIM, BDII, GIP-Validator, and Gratia. MyOSG displays information from many different sources in many different formats. This SLA is inclusive only of selected service used to provide job level decisions or data movement, most notably the XML status based information. A complete list of services presented is in Appendix B.

## Owners
The MyOSG SLA is owned by OSG Operations Center and Indiana University and will be reviewed and agreed upon by the OSG Executive Team.

## Service Name and Description
### Name
GOC Production MyOSG
### Description
The GOC Production MyOSG service presents information from several OSG information sources and presents the information in various forms including web page, Universal Widget API, and XML. The MyOSG service consists of a web server and software consolidators to translate incoming data from several sources to be displayed in MyOSG.

## Security Considerations
MyOSG distributes some private contact information based on certificate authentication. It will be subject to Indiana University institutional policy. Direct access to any of the hardware or software will be restricted to OSG Operations staff. Other OSG staff, upon request and GOC review, may be given access to a development version of MyOSG for experimenting with new software, changes in information providers, or for other testing. OSG Operations reserves the right to allow or not allow such requests based on its internal review.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancement) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The issue causes a full service outage rendering the status information provided by MyOSG used by any other OSG services to move data or submit jobs | The issue causes a full service outage rendering the status information provided by MyOSG used by any other OSG services to move data or submit jobs | The issue causes short (less than 15 minute) periods of unstable or inconsistent performance | The issue causes minor (less than 5 minutes) periods of unstable or inconsistent performance |
| *Number of Clients Affected* | * * | * * | * * |
| The issue affects all MyOSG users | The issue affects a subset of MyOSG users | The issue may or may not affect all MyOSG users | The issue affects only a small number of MyOSG users |
| *Workaround* | * * | * * | * * |
| No workaround will be necessary | No workaround will be necessary | No workaround will be necessary | No workaround will be necessary |
| *Response Time* | * * | * * | * * |
| Within one (1) hour | Issue will be addressed by the next business day | Within the next business day | Within the next business day |
| *Resolution Time* | * * | * * | * * |
| The maximum acceptable resolution time is four (4) continuous hours, after initial response time | The maximum acceptable resolution time is 24 continuous hours, after the initial response time | The maximum acceptable resolution time is five (7) business days | The maximum acceptable resolution time is (30) business days |
| *Escalates Every* | * * | * * | * * |
| One Hour | Two Hour | One Day | One Week |

## Escalation Contacts

| *Escalation Level* | *OSG Contact* |
| ------------------ | ------------- |
| 1st | OSG Operations Infrastructure Lead |
| 2nd | OSG Operations Coordinator |
| 3rd | OSG Production Coordinator |
| 4th | OSG Technical Director and Executive Director |

Detailed information on contacts are viewable on the following [MyOSG URL](https://myosg.grid.iu.edu/rgsummary/index?datasource=summary&summary_attrs_showhierarchy=on&summary_attrs_showservice=on&summary_attrs_showfqdn=on&summary_attrs_showcontact=on&gip_status_attrs_showtestresults=on&gip_status_attrs_showfqdn=on&account_type=cumulative_hours&ce_account_type=gip_vo&se_account_type=vo_transfer_volume&start_type=7daysago&start_date=09/15/2009&end_type=now&end_date=09/15/2009&site_10047=on&rg=on&rg_246=on&gridtype=on&gridtype_1=on&voown=on&voown_25=on&active=on&active_value=1&disable_value=1), and are maintained within
the [OSG Information Management](https://oim.grid.iu.edu) system (for editing purposes only).

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and
at the [Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages
The GOC will strive for 99% service availability. If service availability falls below 99% monthly as monitored by the GOC on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

A maximum of two non-scheduled outages will be accepted by OSG during each six month period of service. If the GOC experiences more than the allotted outage, a service plan will be submitted to the OSG stakeholders with plans to restore the service to an acceptable level of operations.

## Service Support Hours
The MyOSG service is supported 24x7 by the GOC and Indiana University. Critical and High level issues will result in response within (1) hour. All other issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All MyOSG issues should be reported to the GOC immediately by [trouble ticket](http://ticket.grid.iu.edu) web submission. If the problem is deemed critical, a GOC staff member will be alerted immediately.

## Requests for Service Enhancement

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC determination of the necessity and desirability of the enhancement. No alteration or deletions will be brought to the production MyOSG without a minimum of ten (10) business days of testing. New human-interface features or new machine readable interfaces may be brought to production with five (5) business days of testing from the feature requester. The GOC reserves the right to enhance the physical environment of the service based on IU and GOC needs. No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
The GOC provides operators 24x7x365. MyOSG problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
MyOSG Customers agree to:

   * Use the MyOSG to gather information about OSG resources for purposes of VO approved work only.
   * Alert the GOC if they are going to use the MyOSG in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](https://github.com/opensciencegrid/operations/blob/master/SLA/myosg.md#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide critical information within one hour of reporting a critical or high priority incident or one business day for any other criticality.
   * Provide testing for MyOSG-ITB within the time frame defined in the [Requests for Service Enhancements](https://github.com/opensciencegrid/operations/blob/master/SLA/myosg.md#requests-for-service-enhancement) section.
   * Alert the GOC and MyOSG developers when problems are encountered during testing.
   * The customer or GOC will be allowed to request an additional ten (10) business days of testing if problems are encountered or testing is not completed at then end of the initial ten (10) business day testing period. The customer must alert the GOC two (2) business days before the scheduled release if they would like this additional testing time.

### OSG Operations Responsibilities
General responsibilities:
   * Create and add appropriate documentation to the OSG TWiki for appropriate use of MyOSG.
   * Meet response times associated with the priority assigned to Customer issues.
   * Maintain appropriately trained staff.
   * Notify the community of any changes to the machine readable MyOSG pages without (20) business days notification. Notification will be sent to the OSG-Operations mailing list and to each OSG Support Center, along with discussion in the [OSG Operations Meeting](https://github.com/opensciencegrid/operations/blob/master/SLA/ProductionMeetingMinutes).
   * Operations will provide backward compatible views to the best of our ability, due to changes requested in OIM or MyOSG by OSG stakeholders this can not be guaranteed.
   * OSG Operations will provide the legacy VORS view through the life of the OSG Project. This view can be seen at http://myosg.grid.iu.edu/wizardsummary/legacyvorscsv.
   * Insure the compatibility of downtime XML data for six (6) months.
   * The OSG and GOC are not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.

GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.

Database & Application Services responsibilities:
   * Schedule maintenance (downtime) outside of normal business hours (Eastern Time) unless circumstances warrant performing maintenance at another time.
   * Announce and negotiate maintenance with stakeholders to assure minimal interruption to production workload.
   * Alert the community of scheduled maintenance periods at least five business days prior to the start of a service affecting maintenance window.

## Service Measuring and Reporting
The GOC will provide the customer with the following reports in the intervals indicated (monthly, quarterly, semi-annually, or annually):

| *Report Name* | *Reporting Interval* | *Delivery Method* | *Responsible Party* |
| ------------- | -------------------- | ----------------- | ------------------- |
| System Uptime | Monthly | Web Posting | GOC |
| Service Uptime | Monthly | Web Posting | GOC |
| Report of Critical and High Priority Issues | Quarterly | Web Posting | GOC |

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All MyOSG end-users who are members of an OSG VO are considered customers.

# Appendix B - Other Service Dependencies
MyOSG is critically dependent on the following services to serve status information:
   * Local Network, Hardware, OS, Apache and MySQL on the MyOSG instance

MyOSG using the following OSG services to display information but is not directly dependent on their uptime:
   * OIM (Dependent on Replicated OIM Instance; if OIM is down, cached information is used)
   * RSV Data Collection (Dependent on RSV results; if RSV collector or site-RSV-clients are down, then cached information is used)
   * BDII
   * GIP-Validator
   * Gratia (Nebraska Interface)

# Appendix C - Supported Hardware and Software

## Supported Hardware
The following hardware is supported:
   * Physical devices used to provide the MyOSG service.
   * Physical devices used to provide the environment used to house the MyOSG service.
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
Service Provider agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Operations Responsibilities](https://github.com/opensciencegrid/operations/blob/master/SLA/myosg.md#osg-operations-responsibilities) section of this document.

## Software Costs
IU and the Grid Operations Center bears all costs for new and replacement software.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| Rob Quick | OSG Operations Coordinator | 11-10-09 |
| Abhishek Singh Rana <br> (Based on public review by VOs; <br> input from Fermilab-VO & Gratia, <br> NYSGrid, SBGrid, STAR) | VOs Group Coordinator | 12-04-2009 |
| Brian Bockelman | MyOSG Liason / Measurements and Metrics | 11-10-2009 |

# Appendix E - Availability and Reliability Publishing
| Month | Year | Availability | Reliability |
| ----- | ---- | ------------ | ----------- |
| May | 2010 | 100.00% | 100.00% |
| June | 2010 | 100.00% | 100.00% |
| July | 2010 | 99.98% | 99.98% |
| August | 2010 | 99.93% | 99.93% |
| September | 2010 | 99.95% | 100.00% |
| October | 2010 | 99.98% | 99.98% |
| November | 2010 | 99.91% | 99.91% |
| December | 2010 | 99.98% | 99.98% |
| January | 2011 | 99.98% | 99.98% |
| February | 2011 | 99.93% | 99.93% |
| March | 2011 | 99.91% | 99.91% |
| April | 2011 | 99.98% | 99.98% |

   * [[ServiceLevelAgreements#Supporting_Documents][Recent availability statistics]]



