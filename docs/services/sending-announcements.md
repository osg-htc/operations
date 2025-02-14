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
-   A valid OSG user certificate to lookup contacts in the topology database
    -   See [Toplogy and Contacts Data](https://osg-htc.org/operations/services/topology-contacts-data/#contacts-data) for details
-   Local hostname matches DNS
-   DNS forward and reverse lookups in place
```console
[tim@submit-1 topology]$ hostname
submit-1.chtc.wisc.edu
[tim@submit-1 topology]$ host submit-1.chtc.wisc.edu
submit-1.chtc.wisc.edu has address 128.105.244.191
[tim@submit-1 topology]$ host 128.105.244.191
191.244.105.128.in-addr.arpa domain name pointer submit-1.chtc.wisc.edu.
```
-   **(Required for security announcements)** A GPG Key to sign the announcement

Installation
------------

1.  Install the required [Yum repositories](https://opensciencegrid.org/docs/common/yum/#installing-yum-repositories):

1.  Install the OSG tools:

        :::console
        # yum install --enablerepo=devops topology-client

1. If you are on a FermiCloud VM, update `postfix` to relay through FermiLab's official mail server:

        :::console
        echo "transport_maps = hash:/etc/postfix/transport" >> /etc/postfix/main.cf
        echo "*   smtp:smtp.fnal.gov" >> /etc/postfix/transport
        postmap hash:/etc/postfix/transport
        postfix reload

1.  Test this setup by sending a message to yourself only.
    Bonus points for using an email address that goes to a site with aggressive SPAM filtering.

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
| `--oim-recipients <resources|vos>`    | Select contacts associated with resources and/or VOs                                                                    |
| `--oim-contact-type <TYPE>`     | Replacing `<TYPE>` with `administrative` for release announcements or  `security` for security announcements |
| `--bypass-dns-check`            | Use this option to skip the check that one of the host's IP addresses matches with the hostname resolution |


!!! info "Security requirements"
    Security announcements must be signed using the following options:

    - `--sign`: GPG sign the message
    - `--sign-id <KEYID>`: The ID of the key used for singing
    - `--from security`: The mail comes from the OSG Security Team

For release announcements use the following command:

```console
osg-notify --cert your-cert.pem --key your-key.pem \
    --no-sign --type production --message <PATH TO MESSAGE FILE> \
    --subject '<EMAIL SUBJECT>' \
    --recipients "osg-general@opensciencegrid.org osg-operations@opensciencegrid.org osg-sites@opensciencegrid.org vdt-discuss@opensciencegrid.org" \
    --oim-recipients resources --oim-recipients vos --oim-contact-type administrative
```

Replacing `<EMAIL SUBJECT>` with an appropriate subject for your announcement and `<PATH TO MESSAGE FILE>` with the path
to the file containing your message in plain text.
