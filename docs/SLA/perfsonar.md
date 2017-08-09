# OSG PerfSonar Service Level Agreement

## Version Control
| *Version Number* | *Date* | *Author* | *Comments* |
| ---------------- | ------ | -------- | ---------- |
| 1.1 | 9-2-2015 | Scott Teige | First Draft |



## Executive Summary
This SLA is an agreement between OSG Operations and the OSG Management and Stakeholders describing details of the
components of the PerfSonar network monitoring service operated by the GOC.
These components run on hardware at Indiana University and provide data storage and interface capability for the
overall network monitoring service.

## Owners
This SLA is owned by OSG Operations and Indiana University and will be reviewed and agreed upon by the OSG Executive Team and OSG Stakeholders.

## Service Name and Description
### Name
GOC PerfSonar Components

### Description
A preliminary description of the service is available [here](https://docs.google.com/document/d/1l144BSo-88M0cLMMjKcKMIE-Q5s21X-w3lYl-0Pn_08/edit#heading=h.n5qqmobbm4g4) The components
labeled "psds" and "Cassandra" are covered by this agreement.

## Security Considerations

All information collected and distributed by PerfSonar is public.

## Service Target Response Priorities and Response Times

This section deals with unplanned outages. Please see [Requests for Service Enhancement](#requests-for-service-enhancements) for information on planned maintenance outages.

| Critical | High | Elevated | Normal |
| -------- | ---- | -------- | ------ |
| *Work Outage* | * * | * * | * * |
| The PerfSonar Service does not have critical priority | The issue causes a full service outage rendering PerfSonar unavailable | The issue causes data to be inaccessible | The issue causes minor periods of unstable or inconsistent performance |
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
| 3rd | OSG Networking Coordinator |
| 4th | OSG Technical Director and Executive Director |

Detailed information on contacts are viewable on the following [MyOSG URL](http://tinyurl.com/owo4olg),
and are maintained within the [OSG Information Management](https://oim.grid.iu.edu) system (for editing purposes only).

Any ongoing "Normal" or "Elevated" level issues will be discussed at the weekly [Operations](https://github.com/opensciencegrid/operations/tree/master/docs/WeeklyMinutes) and
[Production](https://github.com/opensciencegrid/production/tree/master/docs/WeeklyMinutes) meetings.

## Service Availability and Outages

The GOC will strive for 97% service availability. If service availability falls below 97% monthly as monitored by the GOC on two consecutive months a root cause analysis and service plan will be submitted to the OSG stakeholders for plans to restore an acceptable level of service availability.

## Service Support Hours
The software service is supported 24x7 by the GOC and Indiana University. All issues will be investigated by the next business day.

## Service Off-Hours Support Procedures
All software issues should be reported to the GOC immediately by [trouble ticket](https://ticket.grid.iu.edu/goc/oim) web submission.

## Requests for Service Enhancements

This section deals with planned maintenance outages. Please see [Service Target Response Priorities and Response Times](#service-target-response-priorities-and-response-times) for information on unplanned outages.

The OSG Operations will respond to customer requests for service enhancements based on GOC determination of the necessity and desirability of the enhancement. The GOC reserves the right to enhance the physical environment of the service based on IU and GOC needs. No enhancement will occur without advanced notice to the OSG community.

## Customer Problem Reporting
The GOC provides operators 24x7x365. OIM service problems should be reported immediately by one of the following mechanisms.

   * Creating a problem ticket at https://ticket.grid.iu.edu/goc/oim (*preferred*)
   * Calling the GOC phone at 317-278-9699
   * Emailing a description to goc@opensciencegrid.org

## Responsibilities
### Customer Responsibilities
PerfSonar customers agree to:

   * Use the PerfSonar service for purposes of VO or OSG approved work only.
   * Alert the GOC if they are going to use the Service in a non-standard way, this includes testing or anticipated mass increases in usage.
   * Contact the GOC by means outlined in the [Customer Problem Reporting](#customer-problem-reporting) section of this document if they encounter any service issues.
   * Be willing and available to provide information within one business day for any High level issues reported.
   * Provide testing for the Service within the time frame defined in the [Requests for Service Enhancements](#requests-for-service-enhancements) section.
   * Alert the GOC when problems are encountered during testing.

### Responsibilities

GOC responsibilities:
   * Meet response times associated with the priority assigned to Customer issues.
   * Maintain appropriately trained staff.
   * Announce and negotiate maintenance with stakeholders to assure minimal interruption to normal workload.
   * Alert the community of scheduled maintenance periods at least five (5) business days prior to the start of a service affecting maintenance window.
   * The OSG and GOC are not responsible if a customer does not provide testing during the testing period. In such cases, the GOC has final discretion in what remedial actions to take.
   * Make changes and updates within the normal GOC [release schedule](https://github.com/opensciencegrid/operations/tree/master/docs/SLA/ReleaseSchedule.md)   
   * Perform initial troubleshooting consistent with provided documentation in the event of service failure.
   * Update the [service operations document](https://docs.google.com/document/d/1l144BSo-88M0cLMMjKcKMIE-Q5s21X-w3lYl-0Pn_08/edit#heading=h.n5qqmobbm4g4) when new problems, solutions or troubleshooting methodologies are found.
   * Contact the appropriate parties in the event initial trouble shooting fails to restore service.

Networking Area Coordinator responsibilities:
   * Create and maintain appropriate documentation on the OSG TWiki for appropriate use and troubleshooting of the service.
   * Create and maintain contact information for the components covered by this agreement in OIM.

GOC Service Desk Responsibilities:
   * Log and track all Customer requests for service through the OSG ticketing system.

## Service Measuring and Reporting
The GOC will provide availability data via automated methods, for example, [here](http://tinyurl.com/qz9jm3g).

## SLA Validity Period

This SLA will be in affect for one year.

## SLA Review Procedure

This SLA will renew automatically on a yearly basis unless change or update is requested by the OSG Operations Coordinator, the OSG Executive Team or the Stakeholders.

## References

# Appendix A - Customer Information
All PerfSonar service end-users who are members of an OSG VO, OSG Staff or Networking team members are considered customers.

# Appendix B - Other Service Dependencies
The Service is dependent on the following services to collect and distribute information:
   * Local Network, Hardware, OS and externally supplied software.

# Appendix C - Supported Hardware and Software

## Supported Hardware
The following hardware is supported:
   * Physical devices at Indiana University used to provide the service.
   * Physical devices at Indiana University used to provide the environment used to house the service.

## Hardware Services
The following hardware services are provided:
   * Recommendations. OSG Operations will be responsible for specifying and recommending for purchase or lease hardware meeting customers' needs.
   * Installation. OSG Operations will install, configure and customize system hardware and operating systems.
   * Upgrades. OSG Operations is responsible for specifying and recommending for purchase any hardware upgrades.
   * Diagnosis. OSG Operations will diagnose problems with service related hardware.
   * Repair. OSG Operations analysts are not hardware technicians and receive no training in hardware maintenance, nor do we have the test equipment and tools necessary to do such work.

Performing repairs under warranty: Any work to be performed under warranty may be referred to the warranty service provider at the discretion of the GOC analyst(s). GOC analysts will not undertake work that will void warranties on customer hardware unless specifically requested and authorized by customer's management in writing.

Obtaining repair services: The GOC analyst will recommend a service vendor whenever he/she feels the repair work requires specialized skills or tools.


## Software Services

The GOC agrees to cover software support services, including software installations and upgrades. All software maintenance periods will be announced via the policy put forth in the [OSG Operations Responsibilities](https://github.com/opensciencegrid/operations/blob/master/SLA/oim.md#osg-operations-responsibilities) section of this document.

## Software Costs

The networking team bears all costs for new and replacement software.

# Appendix D - Approval
| *Approved By* | *Position* | *Date* |
| ------------- | ---------- | ------ |
| | | |

# Appendix E - Metric Reports
   * [Recent availability statistics](http://tinyurl.com/qz9jm3g)

