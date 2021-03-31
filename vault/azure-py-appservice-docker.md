---
id: azure-py-appservice-docker
title: Azure Py Appservice Docker
desc: ''
updated: 1617203999400
created: 1617203999400
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure App Service Running Docker Containers on Linux

Starting point for building a web application hosted in Azure App Service from Docker images.

The example shows two scenarios:

- Deploying an existing image from Docker Hub
- Deploying a new custom registry in Azure Container Registry, building a custom Docker image, and running the image from the custom registry

## Running the App

1. Create a new stack:

   ```bash
   $ pulumi stack init dev
   ```

2. Login to Azure CLI (you will be prompted to do this during deployment if you forget this step):

   ```bash
   $ az login
   ```

3. Create a Python virtualenv, activate it, and install dependencies:

   This installs the dependent packages [needed](https://www.pulumi.com/docs/intro/concepts/how-pulumi-works/) for our Pulumi program.

   ```bash
   $ python3 -m venv venv
   $ source venv/bin/activate
   $ pip3 install -r requirements.txt
   ```

4. Specify the Azure location to use:

   ```bash
   $ pulumi config set azure-native:location WestUS
   ```

5. Run `pulumi up` to preview and deploy changes:

   ```bash
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   Resources:
       + 8 created

   Duration: 56s
   ```

6. Check the deployed endpoints:

   ```bash
   $ pulumi stack output helloEndpoint
   http://hello-app91dfea21.azurewebsites.net/hello
   $ curl "$(pulumi stack output helloEndpoint)"
   Hello, world!

   $ pulumi stack output getStartedEndpoint
   http://get-started-15da13.azurewebsites.net
   $ curl "$(pulumi stack output getStartedEndpoint)"
   <html>
   <body>
   <h1>Your custom docker image is running in Azure App Service!</h1>
   </body>
   </html>
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

