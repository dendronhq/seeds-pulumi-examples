---
id: azure-py-appservice
title: Azure Py Appservice
desc: ''
updated: 1617203999399
created: 1617203999399
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

   ```bash
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```bash
   $ az login
   ```

3. Create a Python virtualenv, activate it, and install dependencies:

   This installs the dependent packages [needed](https://www.pulumi.com/docs/intro/concepts/how-pulumi-works/) for our Pulumi program.

   ```bash
   $ python3 -m venv venv
   $ source venv/bin/activate
   $ pip3 install -r requirements.txt
   ```

4. Specify the Azure location to use:

   ```bash
   $ pulumi config set azure-native:location WestUS
   ```

5. Define SQL Server password (make it complex enough to satisfy Azure policy):

   ```bash
   $ pulumi config set --secret sqlPassword <value>
   ```

6. Run `pulumi up` to preview and deploy changes:

   ```bash
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

   ```bash
   $ pulumi stack output endpoint
   https://azpulumi-as0ef47193.azurewebsites.net
   $ curl "$(pulumi stack output endpoint)"
   <html>
       <body>
           <h1>Greetings from Azure App Service!</h1>
       </body>
   </html>
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

