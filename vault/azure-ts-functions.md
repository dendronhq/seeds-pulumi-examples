---
id: azure-ts-functions
title: Azure Ts Functions
desc: ''
updated: 1617203999420
created: 1617203999420
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Deploying Azure Functions

Starting point for building serverless applications hosted in Azure Functions.

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

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   Resources:
       + 8 created

   Duration: 1m18s
   ```

6. Check the deployed endpoint:

   ```
   $ pulumi stack output endpoint
   https://appg-fsprfojnnlr.azurewebsites.net/api/HelloNode?name=Pulumi
   $ curl "$(pulumi stack output endpoint)"
   Hello from Node.js, Pulumi
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [helpers.ts](/assets/helpers.ts)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

