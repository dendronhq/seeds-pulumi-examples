---
id: azure-go-aci
title: Azure Go Aci
desc: ''
updated: 1617203999387
created: 1617203999387
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Container Instances on Linux

Starting point for building web application hosted in Azure Container Instances.

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

3. Set the Azure region location to use:

   ```
   $ pulumi config set azure-native:location westus2
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   Resources:
       + 3 created

   Duration: 1m18s
   ```

5. Check the deployed endpoint:

   ```
   $ pulumi stack output containerIPv4Address
   13.83.66.37
   $ curl "$(pulumi stack output containerIPv4Address)"
   <html>
   <head>
       <title>Welcome to Azure Container Instances!</title>
   </head>
   ...
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

