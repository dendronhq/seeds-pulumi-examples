---
id: classic-azure-py-msi-keyvault-rbac
title: Classic Azure Py Msi Keyvault Rbac
desc: ''
updated: 1617203999446
created: 1617203999446
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Managing Secrets and Secure Access in Azure Applications

[Managed identities](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/) for Azure resources provides Azure services with an automatically managed identity in Azure Active Directory (Azure AD).

This example demonstrates using a managed identity with Azure App Service to access Azure KeyVault, Azure Storage, and Azure SQL Database without passwords or secrets.

The application consists of several parts:

- An ASP.NET Application which reads data from a SQL Database and from a file in Blob Storage
- App Service which host the application. The application binaries are placed in Blob Storage, with Blob Url placed as a secret in Azure Key Vault
- App Service has a Managed Identity enabled
- The identify is granted access to the SQL Server, Blob Storage, and Key Vault
- No secret information is placed in App Service configuration: all access rights are derived from Active Directory

## Running the App

1. Create a new stack:

   ```bash
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```bash
   $ az login
   ```

3. Build and publish the ASP.NET Core project:

   ```bash
   $ dotnet publish webapp
   ```

4. Set an appropriate Azure location like:

   ```bash
   $ pulumi config set azure:location westus
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```bash
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 15 changes performed:
       + 15 resources created
   Update duration: 4m16s
   ```

6. Check the deployed website endpoint:

   ```bash
   $ pulumi stack output endpoint
   https://app129968b8.azurewebsites.net/
   $ curl "$(pulumi stack output endpoint)"
   Hello 311378b3-16b7-4889-a8d7-2eb77478beba@50f73f6a-e8e3-46b6-969c-bf026712a650! Here is your...
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

