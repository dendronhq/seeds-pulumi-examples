---
id: azure-cs-credential-rotation-one-set
title: Azure Cs Credential Rotation One Set
desc: ''
updated: 1617203999379
created: 1617203999379
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Automate the rotation of a secret for resources that use one set of authentication credentials

Modeled after [Microsoft ARM documentation](https://docs.microsoft.com/en-us/azure/key-vault/secrets/tutorial-rotation)

This example demonstrates using a managed identity with Azure App Service to access Azure KeyVault, Azure Storage, and Azure SQL Database without passwords or secrets.

The application consists of several parts:

- A SQL Server to rotate credendials
- A KeyVault that stores the credentials of the SQL Server
- A KeyVault that is only accessible to the WebApp and Function (through Managed Identity)
- An Azure Function that generates a new secret and sets it in SQL Server and Key Vault
- An Azure WebApp that shows that the secret is changing and still accessible
- An EventGrid subscription to receive SecretNearExpiry events from KeyVault and, in turn, call the Azure Function

## IMPORTANT: For example purposes, new secrets are continually generated. Make sure to change the validityPeriod or destory the stack when you are done.

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

3. Build and publish the ASP.NET Core project:

   ```
   $ dotnet publish webapp
   ```

4. Set the Azure region location to use:

   ```
   $ pulumi config set azure-native:location westus2
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   ```

6. Check the deployed website endpoint:

   ```
   $ pulumi stack output WebAppEndpoint
   https://app129968b8.azurewebsites.net/
   $ Start-Process "$(pulumi stack output WebAppEndpoint)"
   ```

7. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

8. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [AppStack.cs](/assets/appstack.cs)
- [Azure.CredentialRotation.OneSet.csproj](/assets/azure-credentialrotation.csproj)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

