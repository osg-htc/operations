
# OSG Service Types

## Introduction

This document is to define expectations for various instances of service machines.
These instance types (discussed below) are: Production, ITB, Development and Utility.

## Production

The availability and maintenance schedule of a production instance is determined
by the Service Level Agreement (SLA) for the service. 

The machine name will be
derived from the service name with no modifiers other than a number indicating
the machine is one of more than one production level instances. An example of a
production machine name is "myosg1.opensciencegrid.org"

## ITB

An ITB instance will meet the SLA requirements of its corresponding production
instance during an announced testing period and not subject to SLA at any other time.

Current maintenance policy states
a production instance cannot be changed without an announcement and a 1 week
testing period. This implies the ITB and production instances of
service machines can be modified independently. A service will not have production
status unless an ITB instance meeting these criteria exists. Outside periods 
governed by SLA, modification and availability of an ITB instance is at the
discretion of the service maintainer/developer.

The period an ITB instance is subject to SLA ends when
the proposed change is released to production or it is known the instance
has failed testing. Either condition is sufficient to define the end of
a testing period.

The machine name will be derived from the service name
with the modifier "itb" and possibly a number indicating the machine is one of
more than one ITB level instances. An example of an ITB machine name is
"myosg-itb1.opensciencegrid.org"

## Development

Development level instances of service machines are optional and at the
discretion of the service maintainer/developer. They are never subject to any SLA and
may or may not exist at any given time. No instance covered by SLA may
depend on any development level machine. 

The machine name will either
not be derived from any service name or will contain a modifier clearly
identifying it as "Development". An example of a development machine name
is "myosg-dev1.grid.iu.edu".

## Utility

A utility machine serves a useful function to a service maintainer/developer.
If one or more production services depend on a utility instance it shall be covered by
the most restrictive SLA of the services dependent on it. An example of a
covered utility machine would be the YUM replica machines operated by the GOC.
Utility machines not covered by SLA include personal VMs used
by staff, "steige.grid.iu.edu", for example.

A utility machine shall be operated
so as to best satisfy the requirements of any dependent services. For example,
the YUM replica are stable and contain fixed content except when being updated
to facilitate upcoming maintenace of their dependent services. Dependence of
service machines on a utility machine may (or may not) be constant in time.
Determination of the dependency status of a utility machine shall be at the
discretion of the corresponding service maintainer/developer.
