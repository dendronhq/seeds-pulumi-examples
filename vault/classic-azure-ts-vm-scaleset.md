---
id: classic-azure-ts-vm-scaleset
title: Classic Azure Ts Vm Scaleset
desc: ''
updated: 1617203999474
created: 1617203999474
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure VM Scale Sets

This example provisions a Scale Set of Linux web servers with nginx deployed, configured the auto-scaling based on CPU load, puts a Load Balancer in front of them, and gives it a public IP address.

## Prerequisites

- [Node.js](https://nodejs.org/en/download/)
- [Download and install the Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
- [Connect Pulumi with your Azure account](https://www.pulumi.com/docs/intro/cloud-providers/azure/setup/) (if your `az` CLI is configured, no further changes are required)

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Configure the app deployment.

   ```
   $ pulumi config set azure:location westus    # any valid Azure region will do
   ```

   Optionally, configure the username and password for the admin user. Otherwise, they will be auto-generated.

   ```
   $ pulumi config set adminUser webmaster
   $ pulumi config set adminPassword <your-password> --secret
   ```

   Note that `--secret` ensures your password is encrypted safely.

3. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

4. Restore NPM dependencies:

   ```
   $ npm install
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing update:
   ...

   Updating:
   ...
   Resources:
       13 created
   Update duration: 2m19s
   ```

6. Check the domain name of the PIP:

   ```
   $ pulumi stack output publicAddress
   dsuv3vqbgi.westeurope.cloudapp.azure.com
   $ curl http://$(pulumi stack output publicAddress)
   #nginx welcome screen HTML is returned
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)

