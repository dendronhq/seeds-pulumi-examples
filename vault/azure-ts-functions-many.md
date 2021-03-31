---
id: azure-ts-functions-many
title: Azure Ts Functions Many
desc: ''
updated: 1617203999422
created: 1617203999422
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Functions in All Supported Languages

Azure Functions created from raw deployment packages in all supported languages.

.NET and Java are precompiled languages, and the deployment artifact contains compiled binaries. You will need the following tools to build these projects:

- [.NET Core SDK](https://dotnet.microsoft.com/download) for the .NET Function App
- [Apache Maven](https://maven.apache.org/) for the Java Function App

Please remove the corresponding resources from the program in case you don't need those runtimes.

## Running the App

1. Build and publish the .NET Function App project:

   ```
   $ dotnet publish dotnet
   ```

2. Build and publish the Java Function App project:

   ```
   $ mvn clean package -f java
   ```

3. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

4. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```
   $ az login
   ```

5. Restore NPM dependencies:

   ```
   $ npm install
   ```

6. Configure the location to deploy the resources to:

   ```
   $ pulumi config set azure-native:location <location>
   ```

7. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing update (dev):
   ...

   Updating (dev):
   ...
   Resources:
       + 20 created
   Duration: 2m42s
   ```

8. Check the deployed function endpoints:

   ```
   $ pulumi stack output dotnetEndpoint
   https://http-dotnet1a2d3e4d.azurewebsites.net/api/HelloDotnet?name=Pulumi
   $ curl "$(pulumi stack output dotnetEndpoint)"
   Hello from .NET, Pulumi
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

