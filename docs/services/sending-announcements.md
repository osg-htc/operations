Sending Announcements
=====================

Various OSG teams need to send out announcement about various events (releases, security advisories, planned changes,
etc).
This page describes how to send announcements using the `osg-notify` tool.

Prerequisites
-------------

To send announcements, the following conditions must be met:

-   A host with an IP address listed in the
    [SPF Record](https://mxtoolbox.com/SuperTool.aspx?action=spf%3aopensciencegrid.org&run=toolpage)
-   A sufficiently modern Linux operating system.
    This procedure has been tested on a FermiCloud Scientific Linux 7 VM and a Linux Mint 18.3 laptop.
    It is known not to work on a FermiCloud Scientific Linux 6 VM.
-   A valid OSG user certificate to lookup contacts in the topology database
-   **(Required for security announcements)** A GPG Key to sign the announcement

Installation
------------

1.  Install the pre-requisites:
    -   Enterprise Linux 7 (first, enable
        [EPEL](https://opensciencegrid.org/docs/common/yum/#install-the-epel-repositories))

            :::console
            yum install git python-requests python2-gnupg

    -   Ubuntu

            :::console
            apt install git python-requests python-gnupg

1.  Install the OSG tools:

        :::console
        git clone https://github.com/opensciencegrid/topology.git

1.  Disable any HTTP proxies by looking in the environment for the following variables and unset them if present:

        :::console
        env | grep -i 'https*_proxy'
        unset HTTPS_PROXY HTTP_PROXY https_proxy http_proxy

1. If you are on a FermiCloud VM, update `postfix` to relay through FermiLab's official mail server:

        :::console
        echo "transport_maps = hash:/etc/postfix/transport" >> /etc/postfix/main.cf
        echo "*   smtp:smtp.fnal.gov" >> /etc/postfix/transport
        postmap hash:/etc/postfix/transport
        postfix reload

5.  Ensure that you can lookup contacts in the topology database by using the `osg-topology` tool to list the contacts:

        :::console
        cd topology
        PYTHONPATH=src python bin/osg-topology --cert publicCert.pem \
            --key privateKey.pem list-resource-contacts

    If the contacts include email addresses, this is working properly.
    If you type your password incorrectly, the authentication will silently fail and you won't get email addresses

Sending the announcement
------------------------

Use the `osg-notify` tool to send the announcement using the relevant options from the following table:

| Option                          | Description                                                                                                  |
|---------------------------------|--------------------------------------------------------------------------------------------------------------|
| `--dry-run`                     | Use this option until you are ready to actually send the message                                             |
| `--cert <FILE>`                 | File that contains your OSG User Certificate                                                                 |
| `--key <FILE>`                  | File that contains your Private Key for your OSG User Certificate                                            |
| `--no-sign`                     | Don't GPG sign the message (release only)                                                                    |
| `--type production`             | Not a test message                                                                                           |
| `--message <FILE>`              | File containing your message                                                                                 |
| `--subject <EMAIL SUBJECT>`     | The subject of your message                                                                                  |
| `--recipients <LIST OF EMAILS>` | List of recipient email addresses, must have at least one                                                    |
| `--oim-recipients resources`    | Select contact associated with resources                                                                     |
| `--oim-contact-type <TYPE>`     | Replacing `<TYPE>` with `administrative` for release announcements or  `security` for security announcements |

!!! info "Security requirements"
    Security announcements must be signed using the following options:

    - `--sign`: GPG sign the message
    - `--sign-id <KEYID>`: The ID of the key used for singing

For release announcements use the following command:

```console
PYTHONPATH=src python bin/osg-notify --cert your-cert.pem --key your-key.pem \
    --no-sign --type production --message message-file
    --subject '<EMAIL SUBJECT>' \
    --recipients "osg-general@opensciencegrid.org osg-operations@opensciencegrid.org osg-sites@opensciencegrid.org vdt-discuss@opensciencegrid.org" \
    --oim-recipients resources --oim-contact-type administrative
```

Replacing `<EMAIL SUBJECT>` with an appropriate subject for your announcement.
