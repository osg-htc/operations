External OASIS Repositories
===========================

We offer hosting of non-OSG CVMFS repositories on OASIS. This means that requests to create, rename, remove, or blanking OASIS repositories will come in as GOC tickets. This document contains instructions for handling those tickets.

!!! note "Also see"
    * [Policy for OSG Mirroring of External CVMFS repositories](https://opensciencegrid.org/technology/policy/external-oasis-repos/)
    * [External OASIS repository](https://opensciencegrid.org/docs/data/external-oasis-repos/)

Requests to Host a Repository on OASIS
--------------------------------------

1.  Ensure that the repository administrator is valid for the VO. This can be done by (a) OSG already having a
    relationship with the person or (b) the contacting the VO manager to find out. Also, the person should be
    listed in the OSG topology [contacts list](https://topology.opensciencegrid.org/contacts).

1.  Review provided URL and verify that it is appropriate for the VO and no other project uses it already. In order to make 
    sure the name in URL is appropriate, check that the name is derived from the VO name or one of its projects.
    Then, add the repository URL to the topology for given VO under the `OASISRepoURLs`. This should cause 
    the repository's configuration to be added to the OSG Stratum-0 within 15 minutes after URL is added into the topology.
    For example, if new URL is for the VO DUNE `http://hcc-cvmfs-repo.unl.edu:8000/cvmfs/dune.osgstorage.org` 
    edit the following under the OASIS section and create PR:

        :::console
        git clone git://github.com/opensciencegrid/topology.git
        vim topology/virtual-organizations/DUNE.yaml
        ...
        OASIS:
          OASISRepoURLs:
          - http://hcc-cvmfs-repo.unl.edu:8000/cvmfs/dune.osgstorage.org/
        ...
     
    When the PR is approved, check on the `oasis.opensciencegrid.org` host whether the new repository was successfuly signed.
    There should be message about it in the log file `/var/log/oasis/generate_whitelists.log`:

    ```
    Tue Sep 25 17:34:02 2018 Running add_osg_repository http://hcc-cvmfs-repo.unl.edu:8000/cvmfs/dune.osgstorage.org
dune.osgstorage.org: Signing 7 day whitelist with masterkeycard... done
    ```

1.  If the respository ends in a new domain name that has not been distributed before, 
    a new domain key will be needed on oasis-replica which should get automatically downloaded from 
    the etc/cvmfs/keys directory in the master branch of the [config-repo github repository](https://github.com/cvmfs-contrib/config-repo).
    There should be a message about downloading it in the log file `/var/log/cvmfs/generate_replicas.log`.
    After the key is downloaded the repository should also be automatically added, with messages in the same log file.

    After the repository is successfully on oasis-replica, in addition you need to update the
    OSG configuration repository.  Make changes in a workspace cloned from the
    [config-repo github repository](https://github.com/cvmfs-contrib/config-repo)
    and use the osg branch (or a branch made from it) in a personal account on `oasis-itb`.
    Add a domain configuration in `etc/cvmfs/domain.d` that's a lot like one of the other imported domains, for example `egi.eu.conf`.
    The server urls might be slightly different; use the URLs of the stratum 1s where it is already hosted if there are any,
    and you can add at least the FNAL and BNL stratum 1s.
    Copy key(s) for the domain into `etc/cvmfs/keys` from the master branch, either a single .pub file or a directory, whichever the master branch has.
    Test all these changes out on the `config-osg.opensciencegrid.org` repository on `oasis-itb`
    using the `copy_config_osg` command, and configure a test client to read from `oasis-itb.opensciencegrid.org`
    instead of `oasis.opensciencegrid.org`.
    Then commit those changes into a new branch you made from the osg branch, and make a pull request.
    Once that PR is approved and merged, log in to the oasis machine and run `copy_config_osg` as root there
    to copy from github to the production configuration repository on the oasis machine.

1.  If the repository name does not match `*.opensciencegrid.org` or `*.osgstorage.org`, skip this step and go on to your next step.
    If it does match one of those two patterns, then respond to the ticket to tell the administrator to continue with their next step (their step 4).  
    We don't want them to continue before 15 minutes has elapsed after step 2 above, so either wait that much time or tell them the time they may proceed (15 minutes after you updated topology).
    Then wait until the admin has updated the ticket to indicate that they have completed their step before moving on. 

1.  Ask the administrator of the BNL stratum 1 (John De Stefano) to also add the new repository. The BNL Stratum-1 administrator
    should set the service to read from
    `http://oasis-replica.opensciencegrid.org:8002/cvmfs/<EXAMPLE.OPENSCIENCEGRID.ORG>`. When the BNL
    Stratum-1 administrator has reported back that the replication is ready, respond to the requester that the repository is
    fully replicated on the OSG and close the ticket.

Requests to Change the URL of an External Repository
----------------------------------------------------

If there is a request to change the URL of an external repository, update the registered value in `OASISRepoURLs` for the respective VO in the topology.  
Tell the requester that it is ready 15 minutes after topology is updated.

Requests to Remove an External Repository
-----------------------------------------

1.  After validating that the ticket submitter is authorized by the VO's OASIS manager, delete the registered value
    for <EXAMPLE.OPENSCIENCEGRID.ORG> in topology for the VO in OASIS Repo URLs.
    Verify that it is removed by running the following on any oasis machine
    to make sure it is missing from the list:

        :::console
        print_osg_repos|grep <EXAMPLE.OPENSCIENCEGRID.ORG>

1.  Check if the repository has been replicated to RAL by looking in their
    [repositories.json](http://cernvmfs.gridpp.rl.ac.uk:8000/cvmfs/info/v1/repositories.json).
    The [user documentation](https://osg-htc.org/docs/data/external-oasis-repos/#removing-a-repository-from-oasis)
    requests the user to make a GGUS ticket to do this, so either ask them to do it or do it yourself.

1.  Add the BNL Stratum-1 operator (John De Stefano) to the ticket and ask him to remove the repository. Wait for
    him to finish before proceeding.

1. Add the FNAL Stratum-1 operators (Merina Albert, Hyun Woo Kim) to the ticket and ask them when they can be ready to delete the repository.
    They can't remove it before it is removed from oasis-replica because their Stratum-1 automatically adds all repositories oasis-replica has.
    However, it has to be done within 8 hours of removal on oasis-replica or an alarm will start going off.

1.  Run the following command on `oasis`, `oasis-itb`, `oasis-replica` and `oasis-replica-itb`:

        :::console
        remove_osg_repository -f <EXAMPLE.OPENSCIENCEGRID.ORG>

1. Tell the FNAL Stratum-1 operators to go ahead and remove the repository.


Response to Security Incident on an External Repository
----------------------------------------

If there is a security incident on the publishing machine of an
external repository and a publishing key is compromised, the
fingerprint of that key should be added to
`/cvmfs/config-osg.opensciencegrid.org/etc/cvmfs/blacklist`.
In addition, another line should be added in the form
`<repository.name NNN` with the repository name and a revision
number that's one higher than the currently published revision.
For more details see the
[cvmfs documentation on blacklisting](https://cvmfs.readthedocs.io/en/stable/cpt-details.html#blacklisting).
