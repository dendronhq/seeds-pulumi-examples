---
id: classic-azure-ts-api-management
title: Classic Azure Ts API Management
desc: ''
updated: 1617203999459
created: 1617203999459
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure API Management

An example Pulumi program that deploys an instance of Azure API Management with the following resources:

- API which is linked to an Azure Function App backend
- Operation and operation policy with URL rewrite and caching rules
- A product, a user, and a subscription to enable access to the API

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

4. Configure Azure location:

   ```
   $ pulumi config set azure:location <location>
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing update (dev):
   ...

   Updating (dev):
   ...
   Resources:
      + 12 created
   Duration: 34m54s
   ```

6. Check the deployed function endpoint:

   ```
   $ pulumi stack output endpoint
   https://greeting-service12345678.azure-api.net/hello/Pulumi
   $ curl --header "Ocp-Apim-Subscription-Key: $(pulumi stack output key)" $(pulumi stack output endpoint)
   {"time":"2019-06-17T15:16:08.227Z","greeting":"Hello Pulumi!"}
   ...
   ```

7. Verify that API caches the response for 30 seconds - the same time should be returned for subsequent queries:

   ```
   $ curl --header "Ocp-Apim-Subscription-Key: $(pulumi stack output key)" $(pulumi stack output endpoint)
   {"time":"2019-06-17T15:16:08.227Z","greeting":"Hello Pulumi!"}
   ...
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

