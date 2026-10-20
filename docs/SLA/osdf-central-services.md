OSDF Central Services Service Level Agreement
=============================================

Service Name(s)
---------------

OSDF (Open Science Data Federation) Director, OSDF Registry

Description
-----------

-  The Director redirects clients requesting or writing objects through the OSDF to the relevant cache or origin
-  The Registry keeps a database of all registered OSDF services and their downtimes

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

If the client uses a SciToken to retrieve a file, the cache may contact the director with the SciToken to determine the
origin that holds the file.

Service Availability
--------------------

#### Availability Definition

   -  Director:
     -  Web engine health API endpoint reports as healthy
     -  Able to redirect a known test object
   -  Registry
      - Web engine health API endpoint reports as healthy
      - Able to retrieve downtimes

#### Target Availability: 95%
