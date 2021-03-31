---
id: classic-azure-ts-serverless-url-shortener-global
title: Classic Azure Ts Serverless URL Shortener Global
desc: ''
updated: 1617203999470
created: 1617203999470
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Globally Distributed Serverless URL Shortener Using Azure Functions and Cosmos DB

Multi-region deployment of Azure Functions and Cosmos DB with Traffic Manager

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

4. Specify the Azure regions to deploy the application:

   ```
   $ pulumi config set locations westus,westeurope
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 23 changes performed:
       + 23 resources created
   Update duration: 21m33.3252322s
   ```

6. Add a short URL:

   ```
   $ pulumi stack output addEndpoint
   https://urlshort-add94ac80f8.azurewebsites.net/api/urlshort-add
   $ curl -H "Content-Type: application/json" \
       --request POST \
       -d '{"id":"pulumi","url":"https://pulumi.com"}' \
       "$(pulumi stack output addEndpoint)"    
   Short URL saved
   ```

7. Query a short URL:

   ```
   $ pulumi stack output endpoint
   http://urlshort-tm.trafficmanager.net/api/
   $ curl -L $(pulumi stack output endpoint)pulumi
   <!doctype html>
   <html lang="en-US" prefix="og: http://ogp.me/ns#">
       <head>
       <title>
           Pulumi
       </title>
   ...
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

