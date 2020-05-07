Installing GRACC Corrections
============================

GRACC Corrections are used to modify records during the summarization process.  RAW records are not modified in the correction process.  The correction is applied after summarization and aggregation, but before the record is enriched with data from [Topology](https://topology.opensciencegrid.org/).

The correction is step 3 in the GRACC summary record workflow:

1. Raw record is received.  The raw record is never modified
2. Summarizer aggregates the raw records
3. Corrections are applied
4. Summarized records are enriched by Topology
5. Summarized and enriched records are uploaded to GRACC

We can currently correct:

* VO Names
* Project Names
* OIM_Site (using the `Host_description` field)

Limitations
-----------

Additional corrections can be written, but some attributes are used to detect duplicate records, and are therefore protected from corrections.  Protected records for summarization are:

    EndTime, RawVOName, RawProjectName, DN, Processors, ResourceType, CommonName,
    Host_description, Resource_ExitCode, Grid, ReportableVOName, ProbeName

For example, we could not write a correction for the `Host_description`.  If we had a correction that changed `Host_description`, then the duplicate detection would not detect the same record during resummarization and it would have duplicate summarized records.

Command Line
------------

The [gracc-correct](https://github.com/opensciencegrid/gracc-tools/tree/master/gracc-correct) tool is used to create, update, and delete corrections.  The tool must be run from a host that can write to GRACC, which is very restricted.  It is recommended to run the _gracc-correct_ tool directly from the gracc.opensciencegrid.org host.

The _gracc-correct_ tool is able to parse new corrections either individually from user input or many at once from a CSV file.

### User Input

Each correction attempts to match one or more attributes of the summarized record in order to set another attribute.

For example, for the VO correction:

    $ gracc-correct vo add
    Field(s) to correct:
        VOName: <vo>
        ReportableVOName: <reportable_vo>
    Corrected VOName: <new_vo_name>

### CSV File

A CSV file can be specified in order to specify multiple corrections in a single batch update.  The CSV file must be of a certain format.

* No Header Row
* The number of columns must be at least the number of matching attribute and the corrected attribute.

For example, a CSV file for VO corrections would be of format:

    VOName,ReportableVOName,CorrectedVOName,....

The CSV file can be specified on the command line with the option `--csv`, for example:

    ./gracc-correct vo add --csv <csv_file>
