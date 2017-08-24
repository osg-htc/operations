# Installing OSG Client

# About This Document

The OSG Cient Tools Package includes:
   * the %LINK_GLOBUS_TOOLKIT% providing client tools for authorization, data transfer and job submission.
   * a list of [[Documentation/GlossaryC#DefsCA][CA]] [[Documentation/GlossaryC#DefsCertificate][Certificates]] trusted by the OSG (installed separately).
   * the [[Documentation/GlossaryC#DefsCRL][Certificate Revocation List]] and tools to keep it current.
   * %LINK_GLOSSARY_CONDOR% client tools for job submission and workflow management.
   * client tools to access a %LINK_GLOSSARY_SRM% provided by a %LINK_GLOSSARY_SE%.





# Engineering Considerations

The OSG Client Tools Package is required on hosts used to submit jobs to the Open Science Grid. We recommend to install the OSG Client Tools on a _dedicated_ job submission host for large scale job submissions to production resources on the OSG. We recommend to use a [public IP address and a fully qualified domain name](#publicipaddress) for shared job submission hosts.


# Requirements

## Host and OS
   * A host to install the OSG Client (pristine node). No grid host certificate is required.
   * OS is %SUPPORTED_OS%
   * Root access

## Certificates
To test and use the installation a valid [[Documentation.CertificateUserGet][grid user certificate]] is required.

## Networking



You'll find more client specific details also in the [Firewall section](#firewall-considerations) of this document.

## Minimum Version

Starting on 11 February 2014, all OSG-issued Digicert certificates (host, service, and personal) use the SHA-2 algorithm. Some software in the Worker Node Client - notably <span style="color: #F60;">dCache SRM client</span> - must be on a recent version to support SHA-2 certificates. Please visit [[SHA2Compliance][our SHA-2 compliance page]] for more information about minimum required versions of software components.


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

If you installed the =osg-client-condor= package, it will also install HTCondor.

If you like, you can see exactly what your version of the OSG client package installed:

<pre class="screen">
</pre>

[[YumRpmBasics#ListDeps][More details on using RPM to see what was installed]]

# Installation and Configuration Procedure




## Install the Client
1. Install the osg-client meta package, which will pull in all dependencies. <pre class="rootscreen">

The client requires no special configuration.
To configure =fetch-crl=, e.g. to use a proxy, check the [[InstallCertAuth#Managing_Certificate_Revocation][CRL documentation]].

## Install HTCondor-G
Optionally, you may want to install HTCondor-G, too.
HTCondor-G is needed to submit jobs directly to the OSG sites.
It is not needed for Glidein-based submission.

1. Install the osg-client-condor meta package, which will pull in all dependencies. <pre class="rootscreen">


# Services
The client is a collection of client programs that do not require service startup or shutdown. The only services are osg-update-certs that keeps uptodate the CA certificates, fetch-crl that keeps uptodate the CRLs and the optional HTCondor-G, only if you installed it.

## Starting and Enabling Services
To start the services:
1. %INCLUDE{"InstallCertAuth" section="OSGBriefFetchCrlStart"}%
1. Optionally, to start HTCondor you can use the service command, e.g.: <pre class="rootscreen">
</pre>

You should also enable the appropriate services so that they are automatically started when your system is powered on:
   * %INCLUDE{"InstallCertAuth" section="OSGBriefFetchCrlEnable"}%
   * Optionally, to enable HTCondor by default on the node: <pre class="rootscreen">
</pre>

## Stopping and Disabling Services
To stop the services:
1. %INCLUDE{"InstallCertAuth" section="OSGBriefFetchCrlStop"}%
1. Optionally, to stop HTCondor you can use: <pre class="rootscreen">
</pre>

In addition, you can disable services by running the following commands. However, you don't need to do this normally.
   * %INCLUDE{"InstallCertAuth" section="OSGBriefFetchCrlDisable"}%
   * Optionally, to disable HTCondor: <pre class="rootscreen">
</pre>

# Firewall Considerations

The %LINK_GLOBUS_TOOLKIT% and %LINK_GLOSSARY_CONDOR% require the client host to _allow_ some inbound and outbound network connections to specific ports. This section describes what additional configuration steps have to be taken if the client host is located behind a firewall. For a more detailed description on firewalls consult [[FirewallInformation][this]] document.

The ranges that you choose below in the Globus and HTCondor configuration must be consistent with the firewall configuration. If the Globus and HTCondor ranges overlap there won't be port collisions but you will need a bigger range.

#PublicIpAddress
## Public IP Address and DNS
If you use the the client host as HTCondor-G submit host for long running jobs, it needs to be reached by remote resources. The easier option is to use a _public_ IP address and not be be located within a private network. For other options check below. To make sure that the client host uses a public IP address and is assigned a fully qualified domain name, use:

<pre class="screen">
Server: 131.215.125.1
Address: 131.215.125.1#53

Name: %RED%%UCL_HOST_FQDN%%ENDCOLOR%
Address: %RED%131.215.114.49%ENDCOLOR%
</pre>

If the client host is not assigned a fully qualified domain name, you can assign the _public IP address_ to the =GLOBUS_HOSTNAME= environment variable:

<pre class="rootscreen">
export GLOBUS_HOSTNAME=%RED%131.215.114.49%ENDCOLOR%
CFG
setenv GLOBUS_HOSTNAME %RED%131.215.114.49%ENDCOLOR%
CFG
</pre>

Make sure to re-login after you update =/etc/profile.d= so that the changes take effect.

## Configuring the firewall and NAT
If the client host is on a private network with NAT or anyway behind a firewall, even a host firewall, the firewall and eventual NAT must be configured correctly.

Assuming you use iptables and chose the port range 20k-25k, you must

Insert the following rules <pre class="file">
-A RH-Firewall-1-INPUT -m state --state NEW -p tcp -m tcp --dport 20000:24999 -j ACCEPT
-A RH-Firewall-1-INPUT -m state --state NEW -p udp -m udp --dport 20000:24999 -j ACCEPT
</pre>
into =/etc/sysconfig/iptables= and <br>
Restart iptables with <pre class="rootscreen">
</pre>


## Globus Port Range

<pre class="rootscreen">
export GLOBUS_TCP_PORT_RANGE=20000,24999
export GLOBUS_TCP_SOURCE_RANGE=20000,24999
CFG
setenv GLOBUS_TCP_PORT_RANGE 20000,24999
setenv GLOBUS_TCP_SOURCE_RANGE 20000,24999
CFG
</pre>

Make sure to re-login after you update =/etc/profile.d= so that the changes take effect.


## HTCondor Port Range
HTCondor-G requires a set of ports open in order to talk to OSG CEs.
If you are running a restrictive firewall, you will need to open O(1k) ports in the firewall and tell HTCondor what port range you opened.


Create =/etc/condor/config.d/10firewall_condor.config= and add <pre class="file">
LOWPORT=20000
HIGHPORT=24999
</pre> to the file and <br>
Restart HTCondor with <pre class="rootscreen">
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
