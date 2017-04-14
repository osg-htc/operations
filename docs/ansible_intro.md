## Ansible in general

Like Puppet, Chef, cfengine, etc., [Ansible](https://www.ansible.com/configuration-management)
is a configuration management tool. Unlike these others, however, Ansible is a client-based solution.
The target machine doesn't check some central Ansible server for instructions. You run Ansible on an
arbitrary local system to make changes on a specific target machine. Ansible runs only when someone
tells it to (though there is a way to make it use a client-server model if you really want). It's basically
like a scripted SSH with lots of bells and whistles. Ansible happens to be written in Python.

### Ansible at Operations

Standardizing configuration management is a long standing goal and we have achieved this goal for 
operational services. Any SLA covered service for which OSGO has responsibility (and OASIS)
can now be installed by any member of the operations staff. Furthermore, this mechanism provides
a standard means to document a service instance in an easily readable and understandable way.

### How it works

Ansible, as implemented at Operations, provides a means to specify and build a VM. The VM host
machine, Operating System, number of CPUs, amount of RAM and size of /usr/local are specified
in a standard way on the master machine. Any data or configuration file
