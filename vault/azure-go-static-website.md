---
id: azure-go-static-website
title: Azure Go Static Website
desc: ''
updated: 1617203999393
created: 1617203999393
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Static Website Using Azure Blob Storage and CDN

This example configures [Static website hosting in Azure Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website).

In addition to the Storage itself, a CDN is configured to serve files from the Blob container origin. This may be useful if you need to serve files via HTTPS from a custom domain (not shown in the example).

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
   $ pulumi config set azure-native:location westus
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   Resources:
       + 9 created
   Duration: 2m52s
   ```

5. Check the deployed website endpoint:

   ```
   $ pulumi stack output staticEndpoint
   https://websitesbc90978a1.z20.web.core.windows.net/
   $ curl "$(pulumi stack output staticEndpoint)"
   <html>
       <body>
           <h1>This file is served from Blob Storage (courtesy of Pulumi!)</h1>
       </body>
   </html>
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

