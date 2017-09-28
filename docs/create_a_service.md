# Adding a new service at the GOC

There are a series of steps needed to create a fully supported service at IU.

## Define the service in ansible

In the following it is assumed you'll be working on collab.grid.iu.edu.
By convention the name of the new service is svc_name.

The steps required to add a new service are:
<pre>
cd install/ansible
# create svc_name.yaml, copy and edit an existng file
svn add svc_name.yaml
# modify the existing inventory files to include the new service
</pre>
The above is the base playbook for creation of a VM

<pre>
cd install/ansible/group_vars
# create svc_name.yaml, copy and edit an existing file
svn add svc_name.yaml
</pre>
This file specifies the operating system version, the number of virtual cores and the allocated memory and disk
space in /usr/local.

<pre>
cd install/ansible/host_vars
# create svc_name.grid.iu.edu.yaml, copy and edit an existng file
svn add svc_name.grid.iu.edu.yaml
</pre>
This file also specifies the operating system version, the number of virtual cores and the allocated memory and disk
space in /usr/local. Additionally, it specifies on which VM host the service VM will be created.

<pre>
cd install/ansible/roles
# create the directory to contain the playbooks for the service
mkdir svc_name
cp -r oasis svc_name
</pre>
This directory typically contains three sub-directories, files, handlers and tasks.

Files is where any required files needed for a VM are located. 60-local-rules for iptables is an example.

Handlers and Tasks contains the actual playbooks used to build the service. Many examples exist and can be consulted.

Finally, build the service machine:
<pre>
cd install
./install.rb svc_name.grid.iu.edu
</pre>
Upon completion the newly made VM should be running on the specified VM host.

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
it have this name or be written in any particular language,
nor is it required to exist in the above directory. If it is not named status_stamp.sh a special file in
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
values are: OK, WARNING, CRITICAL and UNKNOWN. Calculation of the value is service dependent and should
reflect experience to date associated with operation of the service.

The remaining lines may be in any order. filesystem_use is the filesystem reporting the largest
used fraction of all systems on the machine.

In addition to the manditory content, *any* additional information may be included. Commonly included
information includes the results of any tests used to define the service status. For example:
<pre>
condor_running:yes
condor_status returned:96 lines of output
</pre>
would be useful on a service machine dependent on condor for its operation.
Other commonly used fields are:
<pre>
normalized load:7%
Service version:2.1.5-1.osg33.el6
generated:Thu Sep 28 16:16:01 UTC 2017
</pre>
Normalized load is the 5 minute load divided by the number of cores on the machine. Service version (in this example)
is the version of the RPM used to install the service running on the machine. The generated field is
a human readable version of the manditory timestamp field and is, by convention the last field in the status
output.

