---
id: gcp-cs-functions
title: Gcp Cs Functions
desc: ''
updated: 1617203999510
created: 1617203999510
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Google Cloud Functions in Python deployed with C#

This example deploys a Google Cloud Function implemented in Python. Pulumi program is implemented in C#.

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Configure Pulumi for GCP](https://www.pulumi.com/docs/intro/cloud-providers/gcp/setup/)
3. [Install .NET Core 3.0+](https://dotnet.microsoft.com/download)

## Deploying and running the program

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Set the GCP project and region:

   ```
   $ pulumi config set gcp:project <your-gcp-project>
   $ pulumi config set gcp:region <gcp-region>
   ```

3. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 10 changes performed:
       + 10 resources created
   Update duration: 45s
   ```

4. Check the deployed function endpoints:

   ```
   $ pulumi stack output PythonEndpoint
   https://us-central1-test-1234.cloudfunctions.net/python-func-742a512
   $ curl "$(pulumi stack output PythonEndpoint)"
   Hello World!
   ```

5. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

6. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [FunctionsStack.cs](/assets/functionsstack.cs)
- [GCP.Functions.csproj](/assets/gcp.csproj)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

