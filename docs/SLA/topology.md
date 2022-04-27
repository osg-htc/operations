Topology Service Level Agreement
================================

Service Name(s)
---------------

Topology, Topology Web service

Description
-----------

The Topology service holds information about people and resources involved in the OSG. Projects, site resources and downtime information are stored in flat text files in a public GitHub repository. Private data such as contact information is stored in a private repository.

The Topology Web service is a user facing web page that exports topology data.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

Users are required to have a GitHub account and must be whitelisted by OSG Technology group staff in order to request changes in the public repository. Changes to registration are reviewed and applied by OSG staff. Only a limited number of OSG Technology staff members have read and write access to the private contact repository.

Data exported by topology web service publicly readable, but x509 certificate is required to view private contact details (email, phone).

Service Availability
--------------------

#### Availability Definition

<https://topology.opensciencegrid.org/rgdowntime/xml> is accessible

#### Target Availability: 95%
