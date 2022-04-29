Hosted CE Service Level Agreement
================================

Service Name(s)
---------------

Hosted CE

Description
-----------

The Hosted CE (Compute Entrypoint) is a door into a computing site. Sites that prefer not to operate their own CE can request OSG staff to operate one on their behalf. Jobs submitted to CEs are typically pilot jobs submitted from systems such as GlideinWMS, which temporarily reserve compute resources at the site for a given scientific community.

General Service Level Agreement
-------------------------------

<https://osg-htc.org/operations/SLA/general/>

Security Considerations
-----------------------

The Hosted CE requires an SSH credential in order to access the headnode of a site batch system. The site creates dedicated generic user accounts for each scientific community that submits through the CE. Pilot jobs submitted to the CE are authenticated with either GSI or SciTokens.

Service Availability
--------------------

#### Availability Definition

   - Hostcert is valid
   - The CE can be queried with condor_ce_q
   - CE is reporting to Gratia if there are jobs in condor_history

#### Target Availability: 95%
