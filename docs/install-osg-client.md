# Installing OSG Client

# About This Document

This document is for grid users and system administrators. It covers the installation of the OSG Client Tools Package. This package is required on every host used by grid users to submit jobs, transfer data, or interact otherwise with the OSG. Note there is also a Worker Node Client that is not a valid substitute for this package. Likewise the OSG Client cannot replace the Worker Node Client in the batch jobs environment on Worker Node and Compute Element.

The OSG Cient Tools Package includes:
   * the [GLOBUS_TOOLKIT](http://toolkit.globus.org/toolkit/) providing client tools for authorization, data transfer and job submission.
   * a list of CA Certificates trusted by the OSG (installed separately).
   * the Certificate Revocation List and tools to keep it current.
   * HTCondor client tools for job submission and workflow management.
   * client tools to access a Storage Resource Manager provided by a Storage Element.

# Engineering Considerations

The OSG Client Tools Package is required on hosts used to submit jobs to the Open Science Grid. We recommend to install the OSG Client Tools on a *dedicated* job submission host for large scale job submissions to production resources on the OSG. We recommend to use a public IP address and a fully qualified domain name for shared job submission hosts.


# Requirements

## Host and OS
   * A host to install the OSG Client (pristine node). No grid host certificate is required.
   * OS is supported
   * Root access

## Certificates
To test and use the installation a valid [[Documentation.CertificateUserGet][grid user certificate]] is required.

## Networking

You'll find more client specific details also in the [Firewall section](#firewall-considerations) of this document.

## Minimum Version

Starting on 11 February 2014, all OSG-issued Digicert certificates (host, service, and personal) use the SHA-2 algorithm. Some software in the Worker Node Client - notably <pre><span style="color: #F60;">dCache SRM client</span><pre> - must be on a recent version to support SHA-2 certificates.


#ClientContents
# Contents of the OSG Client package

The OSG client may be updated from time to time. As of OSG 3.1.8 in September 2012, the OSG client contains:

   * [[InstallWNClient#WnContents][Everything in the OSG worker node client]]
   * Bandwidth Test Controller (bwctl) client
   * GSI OpenSSH client
   * Globus GRAM clients (including globus-job-run)
   * Globus certificate utilities (including grid-proxy-init)
   * Network Diagnostic Tool (NDT)
   * Nmap (security scanner)
   * One-Way Ping (owamp) client)
   * lcg-info
   * lcg-infosites
   * osg-cert-scripts
   * osg-discovery
   * osg-system-profiler
   * osg-version

If you installed the *osg-client-condor* package, it will also install HTCondor.

If you like, you can see exactly what your version of the OSG client package installed:

<pre class="screen">
[user@client ~]$ rpm -q --requires osg-client
</pre>

# Installation and Configuration Procedure

## Install the Client
1. Install the osg-client meta package, which will pull in all dependencies. 
<pre class="rootscreen">
[root@client ~]$ yum install osg-client
</pre>
The client requires no special configuration.
To configure *fetch-crl*, e.g. to use a proxy, check the [[InstallCertAuth#Managing_Certificate_Revocation][CRL documentation]].

## Install HTCondor-G
Optionally, you may want to install HTCondor-G, too.
HTCondor-G is needed to submit jobs directly to the OSG sites.
It is not needed for Glidein-based submission.

1. Install the osg-client-condor meta package, which will pull in all dependencies. 
<pre class="rootscreen">
[root@client ~]$ yum install osg-client-condor 
</pre>

# Services
The client is a collection of client programs that do not require service startup or shutdown. The only services are osg-update-certs that keeps uptodate the CA certificates, fetch-crl that keeps uptodate the CRLs and the optional HTCondor-G, only if you installed it.
**Avoid to interfere with the system HTCondor. The commands below may start/stop/... also a HTCondor installed outside of the client installation. Be aware of which one you are controlling.**

## Starting and Enabling Services
To start the services:
1. You need to fetch the latest CA Certificate Revocation Lists (CRLs) and you should enable the fetch-crl service to keep the CRLs up to date:
<pre>
# For RHEL 6, CentOS 6, and SL6, or OSG 3 _older_ than 3.1.15 
[root@client ~]$ /usr/sbin/fetch-crl   # This fetches the CRLs 
[root@client ~]$ /sbin/service fetch-crl-boot start
[root@client ~]$ /sbin/service fetch-crl-cron start
# For RHEL 7, CentOS 7, and SL7 
[root@client ~]$ /usr/sbin/fetch-crl   # This fetches the CRLs 
[root@client ~]$ systemctl start fetch-crl-boot
[root@client ~]$ systemctl start fetch-crl-cron
</pre>
1. Optionally, to start HTCondor you can use the service command, e.g.: 
<pre class="rootscreen">
[root@client ~]$ /sbin/service condor start
</pre>
You should also enable the appropriate services so that they are automatically started when your system is powered on:
   * To enable the fetch-crl service to keep the CRLs up to date after reboots:
<pre>
# For RHEL 6, CentOS 6, and SL6, or OSG 3 _older_ than 3.1.15 
[root@client ~]$ /sbin/chkconfig fetch-crl-boot on
[root@client ~]$ /sbin/chkconfig fetch-crl-cron on
# For RHEL 7, CentOS 7, and SL7 
[root@client ~]$ systemctl enable fetch-crl-boot
[root@client ~]$ systemctl enable fetch-crl-cron
</pre>
 * Optionally, to enable HTCondor by default on the node:
<pre>
[root@client ~]$ /sbin/chkconfig condor on
</pre>

## Stopping and Disabling Services
To stop the services:
1. To stop fetch-crl:
<pre>
# For RHEL 6, CentOS 6, and SL6, or OSG 3 _older_ than 3.1.15 
[root@client ~]$ /sbin/service fetch-crl-boot stop
[root@client ~]$ /sbin/service fetch-crl-cron stop
# For RHEL 7, CentOS 7, and SL7 
[root@client ~]$ systemctl stop fetch-crl-boot
[root@client ~]$ systemctl stop fetch-crl-cron
</pre>
1. Optionally, to stop HTCondor you can use: <pre class="rootscreen">
<pre>
[root@client ~]$ /sbin/service condor stop
</pre>

In addition, you can disable services by running the following commands. However, you don't need to do this normally.
   * %INCLUDE{"InstallCertAuth" section="OSGBriefFetchCrlDisable"}%
   * Optionally, to disable HTCondor: <pre class="rootscreen">
</pre>
1. To disable the fetch-crl service:
<pre>
# For RHEL 6, CentOS 6, and SL6, or OSG 3 _older_ than 3.1.15 
[root@client ~]$ /sbin/chkconfig fetch-crl-boot off
[root@client ~]$ /sbin/chkconfig fetch-crl-cron off
# For RHEL 7, CentOS 7, and SL7 
[root@client ~]$ systemctl disable fetch-crl-boot
[root@client ~]$ systemctl disable fetch-crl-cron
</pre>
1. Optionally, to disable HTCondor:
<pre>
[root@client ~]$ /sbin/chkconfig condor off
</pre>

# Firewall Considerations

The GLOBUS TOOLKIT and HTCondor require the client host to *allow* some inbound and outbound network connections to specific ports. This section describes what additional configuration steps have to be taken if the client host is located behind a firewall. For a more detailed description on firewalls consult [[FirewallInformation][this]] document.

The ranges that you choose below in the Globus and HTCondor configuration must be consistent with the firewall configuration. If the Globus and HTCondor ranges overlap there won't be port collisions but you will need a bigger range.

## Public IP Address and DNS
If you use the the client host as HTCondor-G submit host for long running jobs, it needs to be reached by remote resources. The easier option is to use a *public* IP address and not be be located within a private network. For other options check below. To make sure that the client host uses a public IP address and is assigned a fully qualified domain name, use:

<pre class="screen">
[user@client ~]$ hostname -f
client.opensciencegrid.org
[user@client ~]$ nslookup client.opensciencegrid.org
Server:		131.215.125.1
Address:	131.215.125.1#53

Name:           client.opensciencegrid.org
Address:        131.215.114.49
</pre>

If the client host is not assigned a fully qualified domain name, you can assign the *public IP address* to the *GLOBUS_HOSTNAME* environment variable:

<pre class="rootscreen">
[root@client ~]$ cat << CFG >> /etc/profile.d/globus_hostname.sh
export GLOBUS_HOSTNAME=131.215.114.49
CFG
[root@client ~]$ cat << CFG >> /etc/profile.d/globus_hostname.csh
setenv GLOBUS_HOSTNAME 131.215.114.49
CFG
</pre>

Make sure to re-login after you update */etc/profile.d* so that the changes take effect.

## Configuring the firewall and NAT
If the client host is on a private network with NAT or anyway behind a firewall, even a host firewall, the firewall and eventual NAT must be configured correctly.

Assuming you use iptables and chose the port range 20k-25k, you must

Insert the following rules 
<pre class="file">
-A RH-Firewall-1-INPUT -m state --state NEW -p tcp -m tcp --dport 20000:24999 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -p udp -m udp --dport 20000:24999 -j ACCEPT
</pre>
into =/etc/sysconfig/iptables= and <br>
Restart iptables with 
<pre class="rootscreen">
[root@client ~]$ service iptables restart
</pre>
**It is possible to use a client host that is located inside a private network using Network Address Translation. In this case the gatekeeper must be configured to forward incoming connections to the client host. The $GLOBUS_HOSTNAME environment variable must be set to the gatekeeper address. This procedure is currently not documented.**

## Globus Port Range

GRAM can be configured to only use a specified range of TCP ports on the client host for inbound ($GLOBUS_TCP_PORT_RANGE) and outbound ($GLOBUS_TCP_SOURCE_RANGE) connections. More information can be found in the Globus firewall HowTo.
<pre class="rootscreen">
[root@client ~]$ cat << CFG >> /etc/profile.d/globus_firewall.sh
export GLOBUS_TCP_PORT_RANGE=20000,24999
export GLOBUS_TCP_SOURCE_RANGE=20000,24999
CFG
[root@client ~]$ cat << CFG >> /etc/profile.d/globus_firewall.csh
setenv GLOBUS_TCP_PORT_RANGE 20000,24999
setenv GLOBUS_TCP_SOURCE_RANGE 20000,24999
CFG
</pre>

Make sure to re-login after you update /etc/profile.d* so that the changes take effect.


## HTCondor Port Range
HTCondor-G requires a set of ports open in order to talk to OSG CEs.
If you are running a restrictive firewall, you will need to open O(1k) ports in the firewall and tell HTCondor what port range you opened.

HTCondor will only use a specified range of TCP ports for inbound and outbound connections on the client host. This range requires both inbound and outbound connectivity (there are not 2 separate ranges like in the Globus configuration). You can select this range by defining LOWPORT and HIGHPORT in the configuration:

<pre>
LOWPORT=20000
HIGHPORT=24999
</pre> to the file and <br>
Restart HTCondor with 
<pre class="rootscreen">
[root@client ~]$ service condor restart
</pre>

# Test the Client

This document does not cover the usage of the client tools. An introduction how to use the OSG can be found [[Documentation.UsingTheGrid][here]]. A more detailed description how to interact with a %LINK_GLOSSARY_CE% is located [[TestOSGClient][here]].

To simply test the functionality of your installation:
   * make sure your [[CertificateUserGet][grid user certificate]] is installed on the client host
   * make sure all services, including Condor-G if you are using it in the tests, are active (see above)
   * create a [[TestOSGClient#Authentication_using_a_Grid_Prox][grid-proxy]] to test that your certificate is valid
   * create a [[TestOSGClient#Authentication_using_a_VOMS_Prox][voms-proxy]]
   * test to [[TestOSGClient#Mapping_Test][authenticate]] with a %LINK_GLOSSARY_CE%
   * test to [[TestOSGClient#Job_Submission_using_GRAM][submit a job]] using %LINK_GLOSSARY_GRAM%
   * test to [[TestOSGClient#Data_Transfer_Test][transfer data]] using %LINK_GLOSSARY_GRIDFTP%
   * test Condor-G with a [[TestOSGClient#CondorTest][simple job submission]] or follow [[Documentation.CondorSubmittingSingleJob][this tutorial]]

# Getting Help
To get assistance please use this [[HelpProcedure][Help Procedure]].


# References
The OSG Client includes also a set of tools that are part of the [[NetworkPerformanceToolkit][Internet2 Network Performance Toolkit]]

Client installation documents:
   * InstallOSGClient
   * InstallOSGClientTarball
Some components of OSG Client:
   * [[OsgCaManage][osg-ca-manage]]
   * [[InstallCertAuth#Managing_Certificate_Revocation][Install and manage fetch-crl]]
   * [[UpgradeFetchCrl2to3][Differences between frtch-crl and fetch-crl3]]
