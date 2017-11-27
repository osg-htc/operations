External OASIS Repositories
===========================

We offer hosting of non-OSG CVMFS repositories on OASIS. This means that requests to create, rename, remove, or blanking OASIS repositories will come in as GOC tickets. This document contains instructions for handling those tickets.

!!! note "Also see"
    * [Policy for OSG Mirroring of External CVMFS repositories](https://opensciencegrid.github.io/technology/policy/external-oasis-repos/)
    * [External OASIS repository](https://opensciencegrid.github.io/docs/data/external-oasis-repos/)

Requests to Host a Repository on OASIS
--------------------------------------

1.  Ensure that the repository administrator is valid for the VO. This can be done by (a) OSG already having a
    relationship with the person or (b) the contacting the VO manager to find out.  Review the URL and verify verify
    that it is appropriate for the VO.

1.  Add the repository URL in OIM under the VO's OASIS repository URLs. This should cause the repository's configuration
    to be added to the GOC Stratum-0 within 15 minutes.

1.  If the respository ends in a new domain name that has not been distributed before, place a copy of the
    `domain.name.pub` public key from `domain.name` into `/srv/etc/keys` on both `oasis-replica` and
    `oasis-replica-itb`. If you do not have that key, ask the repository service representative how to obtain it.  In
    order to support CVMFS client versions 2.2.X, make a symbolic link of `domain.name.conf`
    `/cvmfs/config-osg.opensciencegrid.org/etc/cvmfs/domain.d` pointing to `default.conf`. This symbolic link has to be
    created on the `oasis-itb` machine's copy of the `config-osg.opensciencegrid.org` repository and then copied to
    production with the `copy_config_osg` command on the oasis machine.

1.  If the repository name matches `*.opensciencegrid.org` or `*.osgstorage.org`, respond to the ticket to ask the
    administrator to continue with their next step, and wait until the admin has updated the ticket to indicate that they
    have completed their step. All other repositories (such as `*.egi.eu`), continue with the next internal step.

1.  Ask the administrator of the BNL stratum 1 to also add the new repository.  The BNL Stratum-1 operator
    should set the service to read from
    `http://oasis-replica.opensciencegrid.org:8000/cvmfs/%RED%example.opensciencegrid.org%ENDCOLOR%`.  When the BNL
    Stratum-1 operator has reported back that the replication is ready, respond to the ticket that the repository is
    fully replicated on the OSG and close the ticket.

Requests to Change the URL of an External Repository
----------------------------------------------------

If there is a request to change the URL of an external repository, update the registered value in OIM for the VO in `OASIS Repo URLs`.

Requests to Remove an External Repository
-----------------------------------------

1.  After validating that the ticket submitter is authorized by the VO's OASIS manager, delete the registered value
    for %RED%example.opensciencegrid.org%ENDCOLOR% in OIM for the VO in OASIS Repo URLs.
1.  Add the FNAL and BNL Stratum-1 operators to the ticket and ask them to remove the repository.  Wait for the
    Stratum-1 operators to finish before proceeding.
1.  Run `cvmfs_server rmfs -f %RED%example.opensciencegrid.org%ENDCOLOR%` and `rm -r
    /oasissrv/cvmfs/%RED%example.opensciencegrid.org%ENDCOLOR%` on `oasis-replica-itb` and `oasis-replica`
1.  Run the following command on `oasis-itb` and `oasis`:

        :::console
        rm -r /srv/cvmfs/%RED%example.opensciencegrid.org%ENDCOLOR%

Requests to Blank an External Repository
----------------------------------------

1.  If there is a need to shut down the distribution of a repository, run `blank_osg_repository` on `oasis-replica` and
    give it the full name of the repository. This will rename the repository directories to a name with the current
    timestamp and replace it with a blank repository.  It includes a step to run on the `oasis` machine, and attempts to
    do it with `ssh`, but if that fails it prints instructions on how to finish by logging in to the `oasis` machine
    manually.
2.  When it is time to put the repository back into production, run `unblank_osg_repository` on `oasis-replica` and
    gives it the full name of the repository again. This will find the directory with the old timestamp and put it back
    into service. This step also attempts to `ssh` to the `oasis` machine.
