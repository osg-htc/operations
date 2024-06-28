Adding External CVMFS Repos
===========================

This document describes how to add an external repo like public-uc.osgstorage.org or ligo.storage.igwn.org.

## Use OSG Docs
Authoritative source for adding new oasis repo is [Install an OASIS Repository](https://osg-htc.org/docs/data/external-oasis-repos/).  Follow instructions starting at heading "Creating a Repository", your first command should be `cvmfs_server mkfs`

When it asks you to open a ticket, if it's an osgstorage.org or opensciencegrid.org domain, then all you need to do is add the CVMFS repo to topology like: https://github.com/opensciencegrid/topology/pull/3986 

Once you have completed adding the fetch-cvmfs-whitelist line to cron, you are done with the OSG documentation.

## Configure the external CVMFS repo

In `/etc/cvmfs/repositories.d/<reponame>/server.conf`, add the lines:
```
CVMFS_COMPRESSION_ALGORITHM=none
CVMFS_GARBAGE_COLLECTION=true
CVMFS_AUTO_GC=true
CVMFS_AUTO_GC_TIMESPAN="2 days ago"
CVMFS_EXTERNAL_DATA=true
CVMFS_AUTO_TAG_TIMESPAN="2 weeks ago"
```
Check in the file for duplicate lines of the above with different settings, comment (`#`) out those lines.

The imporatant line is `CVMFS_COMPRESSION_ALGORITHM`.  If it is set to the default, then CVMFS clients will expect the data to be delivered in compressed format, while the caches will deliver the file in un-compressed format.

## Configure CVMFS-sync

`cvmfs-sync` synchonizes the data from an XRootD server (origin) to a CVMFS repo.

Create a new config file (by copying another existing config) in `/etc/cvmfs-sync`.  The name of the configuration should be `<reponame>.config`

In the config, you will need to modify the repo, source and destination.  This is where cvmfs-sync will scan for new files to add to the CVMFS repo.

### Make the systemd timer
Copy an existing timer like:
```
cp -r /etc/systemd/system/cvmfs-data-update@gwosc.osgstorage.org.service.d /etc/systemd/system/cvmfs-data-update@<reponame>.service.d
```
You may need to edit the override file in the directory above to change the user.

Enable the timer:
```
systemctl enable cvmfs-data-update@public.uc.osgstorage.org.timer
systemctl start cvmfs-data-update@public.uc.osgstorage.org.timer
```

## Checking cvmfs-sync
```
journalctl -u cvmfs-data-update@public.uc.osgstorage.org
```

