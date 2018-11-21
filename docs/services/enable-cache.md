Enable Cache
===============

This document contains information about how to add a cache to be used by OSG clients.

Users will open a help ticket in order for operations to perform the following steps.

Un-Authenticated Cache
----------------------

1.  Open a pull request to add the cache to [`caches.json`](https://github.com/opensciencegrid/StashCache/blob/master/bin/caches.json) file within the StashCache repo.

2. Open a pull request adding the cache to `CVMFS_EXTERNAL_URL` in the  [osgstorage.org.conf](https://github.com/opensciencegrid/oasis-server/blob/master/goc/config-osg/etc/cvmfs/domain.d/osgstorage.org.conf) file.


Authenticated Cache
-------------------

For an authenticated cache, it will need to be added to the specific CVMFS configuration for the authenticated domain.  For example, if it is a LIGO authenticated cache, it will need to be added to the `CVMFS_EXTERNAL_URL` within the `ligo.osgstorage.org.conf` file in the [`config.d`](https://github.com/opensciencegrid/oasis-server/tree/master/goc/config-osg/etc/cvmfs/config.d) directory.  A CMS authenticated cache will need to be added to the `cms.osgstorage.org.conf` file

1. Open a pull request adding the authenticated cache to CVMFS_EXTERNAL_URL in the appropriate domain configuration file within [`config.d`](https://github.com/opensciencegrid/oasis-server/tree/master/goc/config-osg/etc/cvmfs/config.d).


