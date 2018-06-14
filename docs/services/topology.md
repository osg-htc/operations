Topology Service
================

This document contains information about the service that runs <https://topology.opensciencegrid.org> and <https://topology-itb.opensciencegrid.org>.
(These sites are also accessible as <https://my.osg.org> and <https://my-itb.osg.org>.)

The source code for the service is in <https://github.com/opensciencegrid/topology>, in the `src/` subdirectory.
This repository also contains the public part of the data that gets served.


Deployment
----------

Topology is a webapp run with Apache on the host `topology.opensciencegrid.org`.
The same daemon runs both the production and the ITB instances.
The host is a VM at Nebraska;
for SSH access, contact Derek Weitzel or Brian Bockelman.


### Installation

These instructions assume an EL 7 host with the EPEL repositories available.
The software will be installed into `/opt/topology`.
The following steps should be done as root.

1.  Install prerequisites:

        :::console
        # yum install python36 gridsite httpd mod_ssl

1.  Clone the repository:

        :::console
        # cd /opt
        # git clone https://github.com/opensciencegrid/topology

1.  Set up the virtualenv in the clone:

        :::console
        # cd topology
        # python36 -m venv venv
        # . ./venv/bin/activate
        # pip install -r requirements.txt

1.  Configure httpd, mod_wsgi, and mod_gridsite.  The .so file for mod_wsgi is located in `/opt/topology/venv/lib/python3.6/site-packages/mod_wsgi/server/`.

1.  Ensure all the files listed in the section below exist and have the proper permissions.


### File system locations

The following files/directories must exist and have the proper permissions:

| Location                                 | Purpose                                                         | Ownership     | Mode |
| --------                                 | -------                                                         | ---------     | ---- |
| `/opt/topology`                          | Production software install                                     | root:root     | 0644 |
| `/opt/topology-itb`                      | ITB software install                                            | root:root     | 0644 |
| `/etc/opt/topology/config-production.py` | Production config                                               | root:root     | 0644 |
| `/etc/opt/topology/config-itb.py`        | ITB config                                                      | root:root     | 0644 |
| `/etc/opt/topology/bitbucket`            | Private key for contact info repo                               | apache:root   | 0600 |
| `/etc/opt/topology/bitbucket.pub`        | Public key for contact info repo                                | apache:root   | 0644 |
| `~apache/.ssh`                           | SSH dir for Apache                                              | apache:root   | 0700 |
| `~apache/.ssh/known_hosts`               | Known hosts file for Apache                                     | apache:root   | 0644 |
| `/var/cache/topology`                    | Checkouts of topology and contacts data for production instance | apache:apache | 0755 |
| `/var/cache/topology-itb`                | Checkouts of topology and contacts data for ITB instance        | apache:apache | 0755 |

`~apache/.ssh/known_hosts` must contain an entry for `bitbucket.org`;
use `ssh-keyscan bitbucket.org` to get the appropriate entry.


### Software configuration

Configuration is in `/etc/opt/topology/config-production.py` and `config-itb.py`.
The files are in Python format and override default settings in `src/webapp/default_config.py` in the topology repo.

HTTPD configuration is in `/etc/httpd` -- **TODO Derek can you write something here?**


Testing changes on the ITB instance
-----------------------------------

All changes should be tested on the ITB instance before deploying to production.
If you can, test them on your local machine first.
These instructions assume that the code has not been merged to master.

1.  Update the Git clone at `/opt/topology-itb`:

        :::console
        # cd /opt/topology-itb
        # git fetch --all

1.  Check out the branch you are testing from:

        :::console
        # git checkout -b <BRANCH>

1.  If the data format has changed in an incompatible way, edit `/etc/opt/topology/config-itb.py`
    and change `TOPOLOGY_DATA_DIR` and `CONTACT_DATA_DIR` to point to a new directory so the previous data
    does not get overwritten with incompatible data.

1.  Restart `httpd`:

        :::console
        # systemctl restart httpd

1.  Test the web interface at <https://topology-itb.opensciencegrid.org>.

    Errors and output are in `/var/log/httpd/error_log` (for both production and ITB).


### Reverting changes

1.  Switch `/opt/topology-itb` to the previous branch:

        :::console
        # cd /opt/topology-itb
        # git checkout <BRANCH>

1.  If you made config changes to `/etc/opt/topology/config-itb.py`, revert them.

1.  Restart `httpd`:

        :::console
        # systemctl restart httpd

1.  Test the web interface at <https://topology-itb.opensciencegrid.org>.



Updating the production instance
--------------------------------

Updating the production instance is similar to updating ITB instance.

1.  Update master on the Git clone at `/opt/topology`:

        :::console
        # cd /opt/topology
        # git pull origin master

1.  Make config changes to `/etc/opt/topology/config-production.py` if necessary.

1.  Restart `httpd`:

        :::console
        # systemctl restart httpd

1.  Test the web interface at <https://topology.opensciencegrid.org>.

    Errors and output are in `/var/log/httpd/error_log` (for both production and ITB).


### Reverting changes

1.  Switch `/opt/topology` to the previous master:

        :::console
        # cd /opt/topology
        ### (use `git reflog` to find the previous commit that was used)
        # git reset --hard <COMMIT>

1.  If you made config changes to `/etc/opt/topology/config-production.py`, revert them.

1.  Restart `httpd`:

        :::console
        # systemctl restart httpd

1.  Test the web interface at <https://topology.opensciencegrid.org>.


