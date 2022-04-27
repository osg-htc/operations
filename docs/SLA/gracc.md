GRACC Service Level Agreement
=============================

Service Name(s)
---------------

GRACC Frontend, GRACC Data Nodes, GRACC-APEL accounting

Description
-----------

GRACC is a large database of usage information for the OSG.  GRACC includes the collector which receives the raw usage information from multiple sources, the database which stores, ingests, and retrieves the usage, and the Grafana frontend which visualizes the usage.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

GRACC uses several open source components such as ElasticSearch, Grafana, and Kibana.  Each of these components publish security bulletins.  Usernames / passwords are maintained within Grafana to edit the visualization.  Additionally, the data in ElasticSearch is publically available read-only from the web.

Service Availability
--------------------

#### Availability Definition

Queries of various elasticsearch and gracc service statuses return active, web pages are accessible, certificates are valid.

#### Target Availability: 95%
