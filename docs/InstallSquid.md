
# Frontier Squid Caching Proxy Installation Guide


# About This Document

This document is intended for System Administrators who are installing frontier-squid, the OSG distribution of the Frontier Squid software.

# Applicable Versions

The applicable software versions for this document are %RED%OSG Version >= 3.4.0%ENDCOLOR%. The version of frontier-squid installed should be %RED% >= 3.5.24-3.1%ENDCOLOR%. When using an %RED%OSG Version < 3.4.0%ENDCOLOR% and a frontier-squid version in the %RED% 2.7STABLE9 %ENDCOLOR% series, refer to the [old upstream install documentation](https://twiki.cern.ch/twiki/bin/view/Frontier/OldInstallSquid) instead of the current links included below. There are some incompatibilities between the two versions, so if you are upgrading from a 2.7STABLE9 version to a 3.5 version, see the

# About Frontier Squid

Frontier Squid is a distribution of the well-known [squid HTTP caching proxy software](http://squid-cache.org) that is optimized for use with applications on the Worldwide LHC Computing Grid (WLCG). It has

The OSG distribution of frontier-squid is a straight rebuild of the upstream frontier-squid package for the convenience of OSG users.

# Frontier Squid is Recommended

OSG recommends that all sites run a caching proxy for HTTP and HTTPS to help reduce bandwidth and improve throughput. To that end, Compute Element (CE) installations include Frontier Squid automatically. We encourage all sites to configure and use this service, as described below.

For large sites that expect heavy load on the proxy, it may be best to run the proxy on its own host. In that case, the Frontier Squid software still will be installed on the CE, but it need not be enabled. Instead, install your proxy service on the separate host and then configure the CE host to refer to the proxy on that host.

The osg-configure configuration tool (version 1.0.45 and later) warns users who have not added the proxy location to their CE configuration. In the future, a proxy will be required and osg-configure will fail if the proxy location is not set.

# Engineering Considerations

If you will be supporting the Frontier application at your site, review the [upstream documentation Hardware considerations section](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Hardware) to determine how to size your equipment.

# Requirements

## Host and OS
   * OS is %SUPPORTED_OS%.
   * Root access

## Users
The frontier-squid installation will create one user account unless it already exists.

| *User* | *Comment* |
| ------ | --------- |
| squid | Reduced privilege user that the squid process runs under. Set the default gid of the "squid" user to be a group that is also called "squid". |

The package can instead use another user name of your choice if you create a configuration file before installation. Details are in the [upstream documentation Preparation section](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Preparation).

## Networking


The addresses of the WLCG monitoring servers for use in firewalls are listed in the [upstream documentation Enabling monitoring section](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Enabling_monitoring).

# Install Instructions

## Installing Frontier Squid

After meeting the requirements in the previous section, install frontier-squid with this command: <pre class="rootscreen">

Then enable it to start at boot time with this command: <pre class="rootscreen">

# Configuring Frontier Squid

## Configuring the Frontier Squid Service

To configure the Frontier Squid service itself:

1. Follow the [upstream Frontier Squid documentation](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid), in
1. Enable, start, and test the service (as described below)
1. Enable WLCG monitoring as described in the [upstream documentation on enabling monitoring](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Enabling_monitoring) and

## Configuring the OSG CE

To configure the OSG Compute Element (CE) to know about your Frontier Squid service:

1. On your CE host, edit /etc/osg/config.d/01-squid.ini
   * Make sure that enabled is set to True
   * Set location to the hostname and port of your Frontier Squid service (e.g., =my.squid.host.edu:3128=)
   * Leave the other settings at DEFAULT unless you have specific reasons to change them
1. <p>Run osg-configure to propagate the changes on your CE</p> <p><strong>Note:</strong> You may want to finish other CE configuration tasks before running osg-configure. Just be sure to run it once before starting CE services.</p>

# Starting and Stopping the Frontier Squid Service

Starting frontier-squid:
<pre class="rootscreen">
</pre>

Stopping frontier-squid:
<pre class="rootscreen">
</pre>



# Testing Frontier Squid

As any user on another computer, do the following (where %RED%yoursquid.your.domain%ENDCOLOR% is the fully qualified domain name of your squid server):
<pre class="screen">
X-Cache: MISS from %RED%yoursquid.your.domain%ENDCOLOR%
X-Cache: HIT from %RED%yoursquid.your.domain%ENDCOLOR%
</pre>

If the grep doesn't print anything, try removing it from the pipeline to see if errors are obvious. If the second try says MISS again, something is probably wrong with the squid cache writes. Look at the squid [access.log file](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Log_file_contents) to try to see what's wrong.

If your squid will be supporting the Frontier application, it is also good to do the test in the [upstream documentation Testing the installation section](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Testing_the_installation).

# Frontier Squid Log Files

Log file contents are explained in the [upstream documentation Log file contents section](https://twiki.cern.ch/twiki/bin/view/Frontier/InstallSquid#Log_file_contents).
