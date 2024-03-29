---
id: gcp-ts-functions
title: Gcp Ts Functions
desc: ''
updated: 1617203999536
created: 1617203999536
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Google Cloud Functions

An example of deploying an HTTP Google Cloud Function endpoint using TypeScript.

## Prerequisites

0. [Ensure you have the latest Node.js and NPM](https://nodejs.org/en/download/)
1. [Install the Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
2. [Configure Pulumi to access your GCP account](https://www.pulumi.com/docs/intro/cloud-providers/gcp/setup/)

## Running the App

1. Restore NPM dependencies:

   ```
   $ npm install
   ```

2. Create a new stack:

   ```
   $ pulumi stack init gcp-fn
   ```

3. Configure your GCP project and region:

   ```
   $ pulumi config set gcp:project <projectname> 
   $ pulumi config set gcp:region <region>
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 6 changes performed:
       + 6 resources created
   Update duration: 39.65130324s
   ```

5. Check the deployed function endpoint:

   ```
   $ pulumi stack output url
   https://us-central1-pulumi-development.cloudfunctions.net/greeting-function-7f95447
   $ curl "$(pulumi stack output url)"
   Greetings from Google Cloud Functions!
   ```

6. Clean up your GCP and Pulumi resources:

   ```
   $ pulumi destroy
   ...
   $ pulumi stack rm
   ...
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

