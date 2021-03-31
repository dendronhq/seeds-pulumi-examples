---
id: azure-cs-appservice
title: Azure Cs Appservice
desc: ''
updated: 1617203999374
created: 1617203999374
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure App Service with SQL Database and Application Insights

Starting point for building web application hosted in Azure App Service.

Provisions Azure SQL Database and Azure Application Insights to be used in combination
with App Service.

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
   $ pulumi config set azure-native:location centralus
   ```

4. Define SQL Server password (make it complex enough to satisfy Azure policy):

   ```
   pulumi config set --secret sqlPassword <value>
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 10 changes performed:
       + 10 resources created
   Update duration: 1m14.59910109s
   ```

6. Check the deployed website endpoint:

   ```
   $ pulumi stack output Endpoint
   https://azpulumi-as0ef47193.azurewebsites.net
   $ curl "$(pulumi stack output Endpoint)"
   <html>
       <body>
           <h1>Greetings from Azure App Service (courtesy of Pulumi)!</h1>
       </body>
   </html>
   ```

7. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

8. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [AppServiceStack.cs](/assets/appservicestack.cs)
- [Azure.AppService.csproj](/assets/azure.csproj)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

