---
id: azure-ts-appservice
title: Azure Ts Appservice
desc: ''
updated: 1617203999416
created: 1617203999416
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

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

3. Restore NPM dependencies:

   ```
   $ npm install
   ```

4. Set the Azure region location to use:

   ```
   $ pulumi config set azure-native:location westus2
   ```

5. Define SQL Server password (make it complex enough to satisfy Azure policy):

   ```
   pulumi config set --secret sqlPassword <value>
   ```

6. Run `pulumi up` to preview and deploy changes:

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

7. Check the deployed website endpoint:

   ```
   $ pulumi stack output endpoint
   https://azpulumi-as0ef47193.azurewebsites.net
   $ curl "$(pulumi stack output endpoint)"
   <html>
       <body>
           <h1>Greetings from Azure App Service (courtesy of Pulumi)!</h1>
       </body>
   </html>
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

