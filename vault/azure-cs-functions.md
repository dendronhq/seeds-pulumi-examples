---
id: azure-cs-functions
title: Azure Cs Functions
desc: ''
updated: 1617203999380
created: 1617203999380
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Functions on a Linux App Service Plan

Azure Functions created from deployment packages in Python and deployed to an App Service Plan on Linux.

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Install .NET Core 3.1+](https://dotnet.microsoft.com/download)

### Steps

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

3. Configure the location to deploy the resources to:

   ```
   $ pulumi config set azure-native:location <location>
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing update (dev):
   ...

   Updating (dev):
   ...
   Resources:
       + 8 created
   Duration: 2m42s
   ```

5. Check the deployed function endpoints:

   ```
   $ pulumi stack output Endpoint
   https://app1a2d3e4d.azurewebsites.net/api/Hello?name=Pulumi
   $ curl "$(pulumi stack output Endpoint)"
   Hello, Pulumi
   ```

6. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

7. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [Azure.Functions.csproj](/assets/azure.csproj)
- [FunctionsStack.cs](/assets/functionsstack.cs)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

