---
id: classic-azure-go-webserver-component
title: Classic Azure Go Webserver Component
desc: ''
updated: 1617203999441
created: 1617203999441
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Web Server Component Using Azure Virtual Machine

This example provisions a configurable number of Linux web servers in an Azure Virtual Machine, and returns the
resulting public IP addresses. This example uses a reusable [Pulumi component](https://www.pulumi.com/docs/intro/concepts/resources/#components) to simplify the creation of new virtual machines. By
defining a `WebServer` class, we can hide many details (see [here](./webserver.go) for its definition).

## Prerequisites

- [Node.js](https://nodejs.org/en/download/)
- [Download and install the Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
- [Connect Pulumi with your Azure account](https://www.pulumi.com/docs/intro/cloud-providers/azure/setup/) (if your `az` CLI is configured, no further changes are required)

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Configure the deployment. The username and password here will be used to configure the Virtual Machine. The
   password must adhere to the [Azure restrictions on VM passwords](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/faq#what-are-the-password-requirements-when-creating-a-vm).

   ```
   $ pulumi config set azure:location westus  # any valid Azure region will do
   $ pulumi config set username webmaster
   $ pulumi config set password <your-password> --secret
   $ pulumi config set count 5                # optional -- will default to 2 if left out
   ```

   Note that `--secret` ensures your password is encrypted safely.

3. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 15 changes performed:
       + 15 resources created
   Update duration: 4m27s
   ```

5. Check the resulting IP addresses:

   ```
   $ pulumi stack output ipAddresses
   [ 40.112.181.239, ..., 40.112.181.240 ]
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)
- [webserver.go](/assets/webserver.go)

