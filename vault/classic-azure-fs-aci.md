---
id: classic-azure-fs-aci
title: Classic Azure Fs Aci
desc: ''
updated: 1617203999437
created: 1617203999437
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Custom Docker Image running in Azure Container Instances

Starting point for building web application hosted in Azure Container Instances.

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Install .NET Core 3.0+](https://dotnet.microsoft.com/download)

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
   $ pulumi config set azure:location <location>
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 55 changes performed:
       + 10 resources created
   Update duration: 1m56s
   ```

5. Check the deployed container endpoint:

   ```
   $ pulumi stack output endpoint
   https://acifsharp.westeurope.azurecontainer.io
   $ curl "$(pulumi stack output endpoint)"
   <html>
   <head><meta charset="UTF-8">
   <title>Hello, Pulumi!</title></head>
   <body>
       <p>Hello, containers!</p>
       <p>Made with ❤️ with <a href="https://pulumi.com">Pulumi</a></p>
   </body></html>
   ```

6. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

7. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [Azure.Aci.fsproj](/assets/azure.fsproj)
- [Program.fs](/assets/program.fs)
- [Pulumi.yaml](/assets/pulumi.yaml)

