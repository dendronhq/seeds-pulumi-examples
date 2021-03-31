---
id: azure-cs-appservice-docker
title: Azure Cs Appservice Docker
desc: ''
updated: 1617203999376
created: 1617203999376
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure App Service Running Docker Containers on Linux

Starting point for building web application hosted in Azure App Service from Docker images.

The example shows two scenarios:

- Deploying an existing image from Docker Hub
- Deploying a new custom registry in Azure Container Registry, building a custom Docker image, and running the image from the custom registry

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
       + 8 created

   Duration: 56s
   ```

5. Check the deployed endpoints:

   ```
   $ pulumi stack output HelloEndpoint
   http://hello-app-91dfea.azurewebsites.net/hello
   $ curl "$(pulumi stack output HelloEndpoint)"
   Hello, world!

   $ pulumi stack output GetStartedEndpoint
   http://get-started-15da13.azurewebsites.net
   $ curl "$(pulumi stack output GetStartedEndpoint)"
   <html>
   <body>
   <h1>Your custom docker image is running in Azure App Service!</h1>
   </body>
   </html>
   ```

* * *

## Imported Assets

- [Azure.AppService.Docker.csproj](/assets/azure-appservice.csproj)
- [MyStack.cs](/assets/mystack.cs)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

