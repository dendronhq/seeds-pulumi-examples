---
id: azure-py-synapse
title: Azure Py Synapse
desc: ''
updated: 1617203999405
created: 1617203999405
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

   ```bash
   $ pulumi stack init dev
   ```

2. Create a Python virtualenv, activate it, and install dependencies:

   This installs the dependent packages [needed](https://www.pulumi.com/docs/intro/concepts/how-pulumi-works/) for our Pulumi program.

   ```bash
   $ python3 -m venv venv
   $ source venv/bin/activate
   $ pip3 install -r requirements.txt
   ```

3. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```bash
   $ az login
   ```

4. Set the Azure region location to use:

   ```
   $ pulumi config set azure-native:location westus2
   ```

5. Set the user ID to grant access to (e.g., your current user):

   ```
   $ pulumi config set userObjectId $(az ad signed-in-user show --query=objectId | tr -d '"')
   ```

6. Run `pulumi up` to preview and deploy changes:

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

7. Navigate to <https://web.azuresynapse.net> and sign in to your new workspace.

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

