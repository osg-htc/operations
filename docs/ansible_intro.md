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
in a standard way on the master machine. Any data or configuration files needed for the service
are also stored on the master. One or more so-called playbooks specify any action needed to 
build a service machine. These files are all, in turn, checked into an SVN repository and under
version control.

To install a service machine, the running instance (if there is one) is shutdown on the VM host.
By convention, these machines have serial numbers. For example, the current VM for repo1.grid.iu.edu
could be repo1.7. The ansibile installation script is invoked on the master machine and VM hosts are
searched for running instances of the specified service machine. If none are found, a new instance
(with an incremented serial number) is created to the specifications found on the master machine.
Basic OS installation and user creation is handled automaitically. The machine is started and Ansible
completes the installation of the service according to the rules provided in the playbooks.
On completion there is a not running repo1.7 (as a backup) and a newly updated repo1.8.

### Some examples

Follow are excerpts from sundry playbooks and specification files for actual services.

#### Specify a VM
```---
distro: 6
cpus: 2
ram: 2G
disk: 256GB
```

#### Install the basics
```
- name: Cleanup osg-release
  shell: 'rpm -e osg-release'

- name: Install osg 3.3
  shell: 'rpm -U /net/nas01/Public/tmp/osg-3.3-el6-release-latest.rpm'
```

#### Install a list of components

```
- name: Yum install of components needed on production
  yum: state=installed name={{ item }}
  with_items:
    - php
    - php-common
    - php-xml
    - mash
    - xinetd
```

#### Listed actions with multiple parameters

The following pulls files from the master and installs them in specific locations
with specific properties

```
- name: Install machine content
  copy: owner=root group=root mode={{ item.mode }} dest={{ item.dest }} src={{ item.src }}
  with_items:
    - { src: '60-local-repo' ,  dest: '/etc/iptables.d/60-local-repo' , mode: '0744' }
    - { src: 'httpd.conf', dest: '/etc/httpd/conf/httpd.conf', mode: '0644'}
    - { src: 'ifcfg-lo', dest: '/etc/sysconfig/network-scripts/ifcfg-lo', mode: '0644'}
    - { src: 'mash_koji_config', dest: '/etc/mash_koji_config', mode: '0644'}
```

### Service levels (development, ITB, production)

As set up at OSGO, the installation scripts can detect ITB (or dev) instances and production instances.
To the extent possible, the playbooks and configuration files are identical for all levels of service.
When required, specific files can be specified for production/dev and conditional actions taken. Also,
for services with multiple instances (repo1 and repo2, for example) identical commands (other than
the instance number) and identical Ansible files are used to build the instances.

#### An Ansible conditional

```
- name: Yum install of components needed on production
  when: "'-itb' not in inventory_hostname_short"
  yum: state=installed name={{ item }}
  with_items:
    - condor
    - httpd
    - mysql-server
```
