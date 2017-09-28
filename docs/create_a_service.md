# Adding a new service at the GOC

There are a series of steps needed to create a fully supported service at IU.

## Define the service in ansible

## Enable monitoring of the service

### Location of the monitoring source

The existance of a directory here
<pre>
/net/nas01/Public/status/svc_name
</pre>
implies there exists a service machine with the name "svc_name". By convention a copy of
the code that monitors the service exists here. The official copy is maintained by
puppet. Creation of this directory is manditory.

### Define the monitoring code

By convention 
<pre>
/net/nas01/Public/status/svc_name/status_stamp.sh
</pre>
will contain the code that reports the status of a service. It is not required that
it have this name or be written in any particular language. If it does not follow this
convention a special file in
<pre>
/etc/cron.d/
</pre>
must be created to periodically execute the custom status reporting code.

### The format of the monitor report file

There are a few manditory key:value fields in the output of the reporting code. Follows
is the minimum, manditory output:
<pre>
OK
timestamp:1506615361
kernel:2.6.32-696.10.2.el6.x86_64
filesystem_use:/var at 18%
Memory:1020088 kB
Cores:1
</pre>

The first line (which must the the first line of the output) is the reported status. The only allowed
values are: OK, WARNING, CRITICAL and UNKNOWN.

The remaining lines may be in any order and should be clear.
