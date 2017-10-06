# Operations
## Useful documents
[Service Creation](https://github.com/opensciencegrid/operations/blob/master/docs/create_a_service.md)

## Status
### http://monitor.grid.iu.edu/availability/production.html
The overall status of our services can be seen here: [Scott Home page](http://steige.grid.iu.edu/steige/textw.html)

#### Service groups
   * Production
   * ITB
   * Utility
   * Hosts
   * PerfSonar

The status of the individual Service groups can be seen, for example, here:
<pre>
http://monitor.grid.iu.edu/availability/production.html
</pre>
which is made by a cron job on monitor.grid.iu.edu:
<pre>
*/10 * * * * root /usr/local/availability/make_status_board
</pre>

The history of the status is preserved here:
<pre>
 /net/nas01/Public/status_archive
 </pre>
 which contains *many* files with names like this
 <pre>
...
1492917019  1495790419  1498662013  1501535408  1504417816  1507291203
1492917620  1495791020  1498662611  1501536007  1504418419  1507291803
1492918220  1495791619  1498663212  1501536609  1504419016  1507292404
1492918820  1495792219  1498663812  1501537208  1504419616  1507293005
1492919420  1495792821  1498664412  1501537808  1504420218  1507293603
1492920021  1495793420  1498665010  1501538409  1504420816  1507294203
...
</pre>
each of these contains lines like this:
<pre>
...
cobbler:0
collector1:0
collector2:0
collector-itb:0
confluence:0
crlsync:0
csiu:0
csiu-itb:0
data1:0
data2:0
data-itb:0
devm01:0
devm02:0
devm04:0
...
</pre>

#### Goal: Get this into a time series database

## Availability
### http://monitor.grid.iu.edu/availability/avail_24_overview.html
This is created (on monitor.grid.iu.edu) by a cron job running:
<pre>
5 * * * * root /usr/local/availability/make_avail24_board
</pre>

#### Goal: Derive this from the time series database

## Configuration 
### http://steige.grid.iu.edu/steige/service_1506514004.csv
This is created (on steige.grid.iu.edu) by
<pre>
source catalog.sh > /net/nas01/Public/tmp/service_1506514004.csv
</pre>

#### Goal: Time series database

# Common Thread
All of these are derived from the "status_stamp.sh" script that runs on every machine. /etc/cron.d contains (for example)
<pre>
drwxr-xr-x   2 root root  4096 May 16 14:40 .
drwxr-xr-x 124 root root 12288 Oct  6 03:20 ..
-rw-r--r--   1 root root   113 Jul 22  2016 0hourly
-rw-r--r--   1 root root    55 Oct  6 12:25 confsync-dyndns
-rw-r--r--   1 root root   600 Mar 23  2017 fetch-crl
-rw-r--r--   1 root root    97 May 16 14:39 images
-rw-r--r--   1 root root    85 Sep 15  2016 logshare
-rw-r--r--   1 root root    50 Jan 26  2016 munin_ip_plugins
-rw-------   1 root root   222 Sep 22  2014 puppet
-rw-------   1 root root   165 Jul 22  2014 security-test
-rw-r--r--   1 root root   146 Jul 22  2014 setup_munin_cert_age
-rw-r--r--   1 root root   225 May 23  2016 status_stamp
-rw-------   1 root root   235 Oct  6  2016 sysstat
</pre>
where status_stamp contains
<pre>
# Cron job to run /usr/local/status_stamp/status_stamp.sh
# Maintained by Puppet -- editing not recommended

1,16,31,46 * * * * root [[ -x /usr/local/status_stamp/status_stamp.sh ]] && /usr/local/status_stamp/status_stamp.sh
</pre>
and creates a file like this:
<pre>
OK
timestamp:1507293601
uptime:1809855.26
kernel:2.6.32-696.10.1.el6.x86_64
normalized load:0%
filesystem_use:/ at 33%
/boot at 7%
java_running:yes
Memory:131706516 kB
Cores:48
Sizeof /usr/local:48G
generated:Fri Oct  6 08:40:01 EDT 2017
</pre>
[Service Creation](https://github.com/opensciencegrid/operations/blob/master/docs/create_a_service.md) contains details
on how to make a status_stamp.sh script including the constraints on the format of its output.

## Updating a status_stamp_file
The definitive source code is maintained by puppet and exists on the target machine. I like to keep a local copy
here:
<pre>
 /net/nas01/Public/status
 </pre>
 Which, in turn, contains one directory for each service:
 <pre>
backup2         data2        icinga-dev      myosg-itb          psvm01          swamp-ticket      vm08
blogs1          data-itb     idp-itb         oasis              puppet          swamp-ticket-dev  vm09
c267            devm01       imap            oasis2-test        puppet-test     syslog            vm10
cassandra1      devm02       internal        oasis-itb          redirector1     ticket1           voms
cassandra2      devm04       jekyll-dev      oasis-login        redirector2     ticket2           voms-itb
cassandra3      devm05       jira            oasis-login-itb    repo1           ticket-itb        vpn
cassandra-itb1  devm06       jump            oasis-replica      repo2           twiki             web1
cassandra-itb2  display1     lvs1            oasis-replica-itb  repo-itb        twiki-itb         web2
cert            display2     lvs2            oim                rsv             tx1               web-itb
cobbler         display-itb  lvs-itb1        oim-itb            rsv1            tx2               wn1
collector1      dtr-dev      lvs-itb2        osg-flock          rsv2-client     tx-itb1           wn2
collector2      event1       meshconfig      perfsonar2         rsv-client-itb  vm01              wn3
collector-itb   event2       meshconfig-itb  perfsonar-itb      rsv-itb         vm02              xd-login
confluence      event-itb    monitor         psds0              rsvprocess1     vm03              yum-internal-6
crlsync         fw           monitor-itb     psds1              rsvprocess2     vm04              yum-internal-c6
csiu            glidein      munin           psds2              rsvprocess-itb  vm05              yum-internal-c7
csiu-itb        glidein-int  myosg1          psds-itb1          swamp1          vm06
data1           handle-dev   myosg2          psds-itb2          swamp2          vm07
</pre>
On puppet.grid.iu.edu (in scotts home directory as "push_status.sh") is a script that will update a status_stamp.sh file:
<pre>
#!/bin/bash

for arg in "$@"; do
   cp -f /net/nas01/Public/status/$arg/status_stamp.sh /etc/puppet/env/development/modules/status_stamp/files/$arg
done
export EDITOR=emacs
cd /etc/puppet/env/development/
svn commit
cd /etc/puppet/env/testing/
svn update
cd /etc/puppet/env/production/
svn update
</pre>
