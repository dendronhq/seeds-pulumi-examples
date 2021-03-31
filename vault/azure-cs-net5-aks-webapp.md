---
id: azure-cs-net5-aks-webapp
title: Azure Cs Net5 Aks Webapp
desc: ''
updated: 1617203999382
created: 1617203999382
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Deploy Containerized Web Applications using the native Azure Provider, .NET 5, and C# 9

The example demonstrate several Pulumi features:

- Azure-Native provider
- Running on .NET 5
- Using C# 9 constructs like top-level statements, implicit constuctors, and records
- Defining and using components with Pulumi

## Adjust the code

This example can cover several deployments architectures that are listed below.

### Public Docker Image to Azure App Service

You can deploy any public Docker image that contains a web application listening to port 80 to an Azure App Service. Modify the constructor of `MyStack` class in `Program.cs` file to 

```cs
public MyStack()
{
    var app = new WebApplication("hello", new()
    {
        DockerImage = "strm/helloworld-http"
    });

    this.Endpoint = app.Endpoint;
}
```

### Custom Application to Azure App Service

Builds a Docker container from the files in `app` folder, push it to Azure Container Registry, and deploy it to an Azure App Service. Modify the constructor of `MyStack` class in `Program.cs` file to 

```cs
public MyStack()
{
    var app = new WebApplication("hello", new()
    {
        AppFolder = "./app"
    });

    this.Endpoint = app.Endpoint;
}
```

### Public Docker Image to Azure Kubernetes Service

You can deploy any public Docker image that contains a web application listening to port 80 to a new AKS cluster. Modify the constructor of `MyStack` class in `Program.cs` file to 

```cs
public MyStack()
{
    var cluster = new AksCluster("demoaks");

    var app = new WebApplication("hello", new()
    {
        Cluster = cluster,
        DockerImage = "strm/helloworld-http"
    });

    this.Endpoint = app.Endpoint;
}
```

### Custom Application to Azure Kubernetes Service

Builds a Docker container from the files in `app` folder, push it to Azure Container Registry, and deploy it to a new AKS cluster. Modify the constructor of `MyStack` class in `Program.cs` file to 

```cs
public MyStack()
{
    var cluster = new AksCluster("demoaks");

    var app = new WebApplication("hello", new()
    {
        Cluster = cluster,
        AppFolder = "./app"
    });

    this.Endpoint = app.Endpoint;
}
```

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Configure Azure Credentials](https://www.pulumi.com/docs/intro/cloud-providers/azure/setup/)

### Steps

After cloning this repo and making adjustments as described above, from this working directory, run these commands:

1. Create a new stack, which is an isolated deployment target for this example:

   ```bash
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

4. Stand up the application by invoking pulumi

   ```bash
   $ pulumi up
   ```

5. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   $ pulumi destroy --yes
   $ pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [AksCluster.cs](/assets/akscluster.cs)
- [Azure.Dotnet5.csproj](/assets/azure.csproj)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)
- [ResourceGroup.cs](/assets/resourcegroup.cs)
- [WebApplication.cs](/assets/webapplication.cs)

