---
id: gcp-py-cloudrun-cloudsql
title: Gcp Py Cloudrun Cloudsql
desc: ''
updated: 1617203999523
created: 1617203999523
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Deploy Cloud Run instance connected to Cloud SQL

Example of starting a Cloud Run deployment with Cloud SQL instance

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Configure the project:

   ```
   $ pulumi config set gcp:project YOURGOOGLECLOUDPROJECT
   $ pulumi config set gcp:region europe-west1
   $ pulumi config set db-name project-db
   $ pulumi config set --secret db-password SuuperSecret12345!
   ```

3. Preview and deploy changes:
   ```
   $ pulumi up
   ```

4. Curl the Cloud Run:

   ```
   $ curl -H "Authorization: Bearer $(gcloud auth print-identity-token)" $(pulumi stack output cloud_run_url)
   ```

5. Access the database:

   ```
   $ gcloud sql connect $(pulumi stack output cloud_sql_instance_name) -u $(pulumi config get db-name) --project $(pulumi config get gcp:project)
   ```

6. Cleanup

   ```
   $ pulumi destroy
   $ pulumi stack rm
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

