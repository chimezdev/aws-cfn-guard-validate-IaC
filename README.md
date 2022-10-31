# CFN-GUARD

## Investigate the use of Cloud Formation Guard for the automation of Naming Convention check

- Naming convention standard for S3 bucket and values
    - BUCKET NAMING Below are the S3 buckets which will be created for the EDB. 
    - Buckets in the *production environment* have the region identified (such as the string `us-east-2`) in its name to enable cross region replication as needed for certain use cases. At this time, cross region replication is not in use
    - The naming convention followed is `<Company>-<ProgramName>-<EnrichmentLevel>-<Region>-<Environment>`
- Where:
    - Company = ***lly***
    - ProgramName = ***edb***
    - EnrichmentLevel
    ``` raw
        refined
        landing
        conformed
        exploratory
        log
        codeconfig
        Archival
        Athena Results
        Webhosting (Different name for each website)
    ```
    - Region – one of the Lilly AWS regions Example: ***us-east-2***
    - Environment = one of the following
    ```
        dev
        qa
        prod
    ```
- Investigate extraction of S3 bucket from template
    - sample code template with in comement of RITM
    `!sub arn:aws:s3:::lly-edp-refined-us-east-2-${pBucketPrefix}/gss_ephub/* #R1TM3662644`

- Recommedation from jason
Based on the naming conventions we want to enforce this can potentially be handled by CloudFormation Guard. That should help support most situations, the key is knowing exactly which resources to enforce requirements