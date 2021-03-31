---
id: azure-ts-synapse
title: Azure Ts Synapse
desc: ''
updated: 1617203999425
created: 1617203999425
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Synapse Workspace and Pools

Starting point for enterprise analytics solutions based on Azure Synapse.

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

   ```bash
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   Resources:
       + 13 created

   Duration: 10m53s
   ```

6. Navigate to <https://web.azuresynapse.net> and sign in to your new workspace.

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

