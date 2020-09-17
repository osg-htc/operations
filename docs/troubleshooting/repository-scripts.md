Troubleshooting Guide for Yum Repository Scripts
================================================


The *repo.opensciencegrid.org* and *repo-itb.opensciencegrid.org* hosts contain the OSG Yum software repositories plus related services and tools. In particular, the *mash* software is used to download RPMs from where they are built (at the University of Wisconsin–Madison), and there are some associated scripts to configure and invoke *mash* periodically. Use this guide to monitor the *mash* system for problems and to perform basic troubleshooting when such problems arise.

Monitoring 
----------

To monitor the repository hosts for proper *mash* operation, do the following steps on each host:

   1. `ssh` to repo.opensciencegrid.org and `cd` into `/var/log/repo` to view logs from *mash* updates
   1. Examine the “Last modified” timestamp of all of the *update\_repo.\*.log* files
   1. If the timestamps are all less than 2 hours old, life is good and you can skip the remaining steps below
   1. Otherwise, examine the “Last modified” timestamp of the *update\_all\_repos.err* file
   1. If the *update\_all\_repos.err* timestamp is current, there may be a *mash* process that is hung; see the [Troubleshooting steps below](#troubleshooting-and-mitigation)
   1. If **all** timestamps are more than 6 hours old, something may be wrong with cron or its mash entries:
      1. Verify that cron is running and that the cron entries for mash are still present; if not, try to restore things
      1. Otherwise, create a Freshdesk ticket with a subject like “Repo update logs are too old on <HOST>” and with relevant details in the body
      1. Assign the ticket to the “Software” group

Troubleshooting and Mitigation
------------------------------

### Identifying and fixing a hung mash process

If a mash update process hangs, all future invocations from cron of the mash scripts will exit without taking action because of the hung process. Thus, it is important to identify and remove any hung processes so that future updates can proceed. Use the procedure below to remove any hung mash processes; doing so is safe in that it will not adversely affect the Yum repositories being served from the host.

1. In the listing of log files (see above), view the file =update_all_repos.err=
1. In the error log file, look for messages such as:  

        :::file
        Wed Jan 20 18:10:02 UTC 2016: **Can't acquire lock, is update_all_repos.sh already running?**  
 
    This message indicates that the most recent update attempt quit early due to the presence of a lock file, most likely from a hung *mash* process.
 
1. Look for *mash* processes:  
   
        :::console
        root@host # ps -C mash -o pid,ppid,pgid,start,command
          PID  PPID  PGID  STARTED COMMAND
        24551 24549 23455  Jan 15 /usr/bin/python /usr/bin/mash osg-3.1-el5-release -o
        24552 24551 23455  Jan 15 /usr/bin/python /usr/bin/mash osg-3.1-el5-release -o
   
1. If there are *mash* processes that started on a previous date or more than 2 hours ago, it is best to remove their corresponding process groups (PGID above):  
    
        :::console
        root@host # kill -TERM -23455
       
    Then verify that the old processes are gone using the same *ps* command as above:

        :::console  
        root@host # ps -C mash -o pid,ppid,pgid,start,command
        PID  PPID  PGID  STARTED COMMAND

1. If any part of this process does not look or work as expected:
   1. Create a GOC ticket with a subject like “Problems with mash on repo<strong>N</strong>” and with relevant details in the body
   1. Assign the ticket to “Software Support (Triage)”
   1. Email Carl Edquist <edquist@cs.wisc.edu> and CC Tim Cartwright <cat@cs.wisc.edu> with the ticket URL
