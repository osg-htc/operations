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

In the case of a GitHub pull request, you will need to provide IDs using the `next_*_id` tools in the Topology
[bin/ dir](https://github.com/opensciencegrid/topology/tree/master/bin) and potentially fix-up other data.
To assist the user, do one of the following, depending on the severity of the fixes required for the PR:

- For minor issues, submit a "Comment" review using
  [GitHub suggestions](https://help.github.com/en/articles/commenting-on-a-pull-request#adding-line-comments-to-a-pull-request)
  and ask the user to [incorporate your suggestions](https://help.github.com/en/articles/incorporating-feedback-in-your-pull-request).
- For major issues, create a branch based off of their PR, make changes, and submit your own PR that
  [closes](https://help.github.com/en/articles/closing-issues-using-keywords) the original user's PR.

The CI checks should catch most errors but you should still review the YAML changes.
Certain things to check are:

-   Do contact names and IDs match what's in the contacts data?
    (See below for instructions on how to get that information.)
    If the person is not in the contacts data, you will need to add them before approving the PR.

-   Is the PR submitter authorized to make changes to that project/VO/resource?
    Can you match them to a person affiliated with that project/VO/site?
    (The contacts data now includes the GitHub usernames for some people.
    See below for instructions on how to get that information.)

-   Is their GitHub ID registered in the [contact database](#contacts-data) and are they associated with the relevant
    resource, site, facility, or VO?


### Retiring resources

A resource can be disabled in its topology yaml file by setting `Active: false`.
However the resource entry should not be immediately deleted from the yaml file.

One reason for this is that the WLCG accounting info configured for resources is used to determine which resources to
send APEL numbers for.
Removing resources prematurely could prevent resummarized GRACC data from getting sent appropriately.

Resources that have been inactive for at least two years are eligible to be deleted from the topology database.
The GRACC records for this resource can be inspected in [Kibana](https://gracc.opensciencegrid.org/kibana).

-   In the search bar, enter `ProbeName:*\:FQDN` in the search bar, where `FQDN` is the FQDN defined for your resource

    For example, if your resource FQDN is `cmsgrid01.hep.wisc.edu` you would enter `ProbeName:*\:cmsgrid01.hep.wisc.edu`

-   In the upper-right corner, use the Time Range selection to pick "Last 2 years"

With this criteria selected, Kibana will show you if it has received any records for this resource in the past two
years.

If there are no records returned, you may remove the resource from the resource group yaml file in the topology repo.
Any downtime entries for this resource in the corresponding downtime yaml file for the resource group must be removed
also.
If you remove the last resource in the resource group yaml file, you should remove the resource group and corresponding
downtime yaml files as well.


### Reviewing project PRs

New projects are typically created by the Research Facilitation team.
Here are a few things to check:

-   Does the "Name" in the YAML match the file name of the project?

-   Did osg-bot warn about a "New Organization"?
    If so, search around in the projects directory and make sure the "Organization" in the YAML
    is not a typo or alternate spelling for an existing organization.
    grep around in the `/projects/` directory for substrings of the organization.
    For example, if the new org is "University of Wisconsin Madison", do:
    
    	:::command
    	$ grep -i wisconsin projects/*.yaml
    	
    and you will see that it's supposed to be "University of Wisconsin-Madison".
    
    If the new organization is not a typo or alternate spelling,
    dismiss osg-bot's review with the comment "new org is legit".

-   Is the project name is of the form `<INSTITUTION>_<PINAME>`, e.g. `UWMadison_Parks`?
    (This is recommended but not required for new projects.)
    If so:
    
    Is the short name -> organization mapping for the institution in `/mappings/project_institution.yaml`
    (e.g. `UWMadison: "University of Wisconsin-Madison"`)?
    If not, ask the PR author to add it.

-   Does the "FieldOfScience" in the YAML match one of the keys in `/mappings/nsfscience.yaml`?
    (The list is also available on the _left_ column of [this CSV](https://topology.opensciencegrid.org/nsfscience/csv).)

-   Is the "ID" unique?

-   Is the "Sponsor" correct?  The sponsor depends on where the users will be submitting jobs from:

    -   If they primarily submit from some CI Connect interface such as "OSG Connect", use:

            :::yaml
            Sponsor:
                CampusGrid:
                    Name: <CAMPUS_GRID>

        The campus grid name must be one of the ones in the `/projects/_CAMPUS_GRIDS.yaml` file..

    -  Otherwise, the project must be sponsored by a VO:

            :::yaml
            Sponsor:
                VirtualOrganization:
                    Name: <VO>

        The VO name must be one of the ones in the `/virtual-organizations/` dir.


Contacts Data
-------------

The OSG keeps contact data for administrators and maintainers of OSG resources and VOs for the purpose of distributing
security, software, and adminstrative (e.g., OSG All-Hands dates) announcements.
Additionally, OSG contacts have the following abilities:

- View other contacts' information (via [HTML](https://topology.opensciencegrid.org/contacts) and
  [XML](https://topology.opensciencegrid.org/miscuser/xml)) with a registered certificate
- [Register resource downtimes](https://opensciencegrid.org/docs/common/registration/#registering-resource-downtimes)
  for resources that they are listed as an administrative contact, if they have a registered GitHub ID

Contact data is kept as editable YAML in <https://bitbucket.org/opensciencegrid/contact/>, in `contacts.yaml`.
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

!!! danger
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

!!! danger
    Any new contacts need to have their association with the OSG verified by a known contact within the relevant VO,
    site, or project.

When registering a new contact, first obtain the required
[contact information](https://opensciencegrid.org/docs/common/registration/#registering-contacts).

After obtaining this information and verifying their association with the OSG, fill out the values in
`template-contacts.yaml` and add it to `contacts.yaml`.
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

!!! important
    If you change the contact's `FullName`, you **must** make the same change to every place that the contact
    is mentioned in the `topology` repo.
    Get the contact changes merged in first.
