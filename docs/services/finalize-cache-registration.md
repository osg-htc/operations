Finalizing New Cache Registration
=================================

Once a new cache is registered with OSG, there are additional operations tasks that
must be performed before it is usable by clients.

The steps on this page are for OSG Operations; sysadmins should follow the
[cache registration document](https://opensciencegrid.org/docs/data/stashcache/install-cache/)
and open a support ticket to have these steps executed.

Un-Authenticated Cache
----------------------

1.  Test to make sure the cache is working by executing the following:

    ```console
    $ curl http://hcc-stash.unl.edu:8000/user/rynge/public/test.txt
    Hello!
    ```

2.  Open a pull request to add the cache to [`caches.json`](https://github.com/opensciencegrid/StashCache/blob/master/bin/caches.json) file within the StashCache repo.

3. Open a pull request adding the cache to `CVMFS_EXTERNAL_URL` in the  [osgstorage.org.conf](https://github.com/opensciencegrid/oasis-server/blob/master/goc/config-osg/etc/cvmfs/domain.d/osgstorage.org.conf) file.

Authenticated Cache
-------------------

For an authenticated cache, it will need to be added to the specific CVMFS configuration for the authenticated domain.  For example, if it is a LIGO authenticated cache, it will need to be added to the `CVMFS_EXTERNAL_URL` within the `ligo.osgstorage.org.conf` file in the [`config.d`](https://github.com/opensciencegrid/oasis-server/tree/master/goc/config-osg/etc/cvmfs/config.d) directory.  A CMS authenticated cache will need to be added to the `cms.osgstorage.org.conf` file

1. Open a pull request adding the authenticated cache to `CVMFS_EXTERNAL_URL` in the appropriate domain configuration file within [`config.d`](https://github.com/opensciencegrid/oasis-server/tree/master/goc/config-osg/etc/cvmfs/config.d).

2. Coordinate with the VO to test that authorization works.  As each VO is expected to export a different directory and require different authorizations, a custom test
   must be arranged each time.

