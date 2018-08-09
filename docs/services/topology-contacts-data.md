Topology and Contacts Data
==========================

This is internal documentation intended for OSG Operations staff.
It contains information about the data provided by <https://topology.opensciencegrid.org>.

The topology data for the service is in <https://github.com/opensciencegrid/topology>, in the `projects/`, `topology/`, and `virtual-organizations/` subdirectories.
The contacts data is in <https://bitbucket.org/opensciencegrid/contact/>, in `contacts.yaml`.


Topology Data
-------------

Admins may request changes to data in the topology repo via either a GitHub pull request or a Freshdesk ticket.
These changes can be to a project, a VO, or a resource.
The [registration document](https://opensciencegrid.org/docs/common/registration) and
[topology README document](https://github.com/opensciencegrid/topology/README.md) should tell them how to do that.

The CI checks should catch most errors but you should still review the YAML changes.
Certain things to check are:

-   Do contact names and IDs match what's in the contacts data?
    (See below for instructions on how to get that information.)
    If the person is not in the contacts data, you will need to add them before approving the PR.

-   Is the PR submitter authorized to make changes to that project/VO/resource?
    Can you match them to a person affiliated with that project/VO/site?
    (The contacts data now includes the GitHub usernames for some people.
    See below for instructions on how to get that information.)


Contacts Data
-------------

Contacts data is either available as XML in <https://topology.opensciencegrid.org/miscuser/xml> or
editable YAML in <https://bitbucket.org/opensciencegrid/contact/>, in `contacts.yaml`.
The YAML file contains sensitive information and is only visible to people with access to that repo.


### Getting access to the contact repo

The contacts repo is hosted on BitBucket.
You will need an Atlassian account for access to BitBucket.
The account you use for OSG JIRA should work.
Once you have an account, request access from Brian Lin, Mat Selmeci, or Derek Weitzel.
You should then be able to go to <https://bitbucket.org/opensciencegrid/contact/>.


### Using the contact repo

BitBucket is similar to GitHub except you don't make a fork of the contact repo,
you just clone it to your local machine.
This means that any pushes go directly to the main repo instead of your own fork.

!!!note
    Don't push to master.
    For any changes, always create your own branch, push your changes to that branch, then make a pull request.
    Have someone else review and merge your pull request.

All contact data is stored in `contacts.yaml`.
The contact info is keyed by a 40-character hexadecimal ID which was generated from their email address when they were first added.
An example entry is:
```yaml
25357f62c7ab2ae11ddda1efd272bb5435dbfacb:
# ^ this is their ID
  FullName: Example A. User
  Profile: This is an example user.
  GitHub: ExampleUser
  # ContactInformation data requires authorization to view
  ContactInformation:
    DNs:
    - ...
    IM: ...
    PrimaryEmail: user@example.net
    PrimaryPhone: ...
```

When making changes to the contact data, first see if a contact is already in the YAML file.
Search the YAML file for their name.
Be sure to try variations of their name if you don't find them --
someone may be listed as "Dave" or "David", or have a middle name or middle initial.

Follow the instructions below for adding or updating a contact, as appropriate.


#### Adding a new contact

Before adding a new contact, verify their VO, site, or project affiliation,
and get some brief profile information about them.
The profile does not need to be detailed -- examples are "Neutrino physicist at Fermilab working on the DUNE project"
or "Administrator for GridUNESP CEs."

After obtaining this information, fill out the values in `template-contacts.yaml` and add it to `contacts.yaml`.
To get the hash used as the ID, run `email-hash` on their email address.
For example:

```command
$ cd contact  # this is your local clone of the "contact" repo
$ bin/email-hash user@example.net
25357f62c7ab2ae11ddda1efd272bb5435dbfacb
```
Then your new entry will look like
```yaml
25357f62c7ab2ae11ddda1efd272bb5435dbfacb:
    FullName: Example A. User
    ....
```

The `FullName` and `Profile` fields in the main section,
and the `PrimaryEmail` field in the `ContactInformation` section are required.
The `PrimaryEmail` field in the `ContactInformation` section should match the hash that you used for the ID.

In addition, if they will be making pull requests against the topology repo,
e.g. for updating site information, reporting downtime, or updating project or VO information,
obtain their GitHub username and put it in the `GitHub` field.


#### Editing a contact

Once you have found a contact in the YAML file, edit the attributes by hand.
If you want to add information that is not present for that contact, look at `template-contacts.yaml` to find out what the attributes are called.

!!!note
    The ID of the contact never changes, even if the user's `PrimaryEmail` changes.

!!!note
    If you change the contact's `FullName`, you **must** make the same change to every place that the contact
    is mentioned in the `topology` repo.
    Get the contact changes merged in first.

