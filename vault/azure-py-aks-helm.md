---
id: azure-py-aks-helm
title: Azure Py Aks Helm
desc: ''
updated: 1617203999397
created: 1617203999397
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Kubernetes Service (AKS) Cluster and Helm Chart

This example demonstrates creating an [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/)
cluster and deploying a Helm Chart from [Bitnami Helm chart repository](https://github.com/bitnami/charts)
into this cluster, all in one Pulumi program.

The example showcases the [native Azure provider for Pulumi](https://www.pulumi.com/docs/intro/cloud-providers/azure/).

## Prerequisites

- Install [Pulumi](https://www.pulumi.com/docs/get-started/install/).

- Install [Python 3.6](https://www.python.org/downloads/) or higher.

- We will be deploying to Azure, so you will need an Azure account. If
  you do not have an account, [sign up for free here](https://azure.microsoft.com/en-us/free/).

- Setup and authenticate the [native Azure provider for Pulumi](https://www.pulumi.com/docs/intro/cloud-providers/azure/setup/).

## Running the Example

In this example we will provision a Kubernetes cluster running a
public Apache web server, verify we can access it, and clean up when
done.

1. Get the code:

   ```bash
   $ git clone git@github.com:pulumi/examples.git
   $ cd examples/azure-py-aks-helm
   ```

2. Create a new stack, which is an isolated deployment target for this example:

   ```bash
   $ pulumi stack init
   ```

3. Set the required configuration variables for this program:

   ```bash
   $ pulumi config set azure-native:location westus2
   ```

4. Deploy everything with the `pulumi up` command. This provisions
   all the Azure resources necessary, including an Active Directory
   service principal, AKS cluster, and then deploys the Apache Helm
   Chart, all in a single gesture (takes 5-10 min):

   ```bash
   $ pulumi up
   ```

   Note: this command will create a virtual environment and restore
   dependencies automatically as described in [Pulumi
   docs](https://www.pulumi.com/docs/intro/languages/python/#virtual-environments).

5. Now your cluster and Apache server are ready. Several output
   variables will be printed, including your cluster name
   (`cluster_name`), Kubernetes config (`kubeconfig`) and server IP
   address (`apache_service_ip`).

   Using these output variables, you may access your Apache server:

   ```bash
   $ curl $(pulumi stack output apache_service_ip)
   <html><body><h1>It works!</h1></body></html>
   ```

   And you may also configure your `kubectl` client using the
   `kubeconfig` configuration:

   ```bash
   $ pulumi stack output kubeconfig --show-secrets > kubeconfig.yaml
   $ KUBECONFIG=./kubeconfig.yaml kubectl get service

   NAME           TYPE           CLUSTER-IP     EXTERNAL-IP      PORT(S)                      AGE
   apache-chart   LoadBalancer   10.0.154.121   40.125.100.104   80:30472/TCP,443:30364/TCP   8m
   kubernetes     ClusterIP      10.0.0.1       <none>           443/TCP                      8m
   ```

6. At this point, you have a running cluster. Feel free to modify
   your program, and run `pulumi up` to redeploy changes. The Pulumi
   CLI automatically detects what has changed and makes the minimal
   edits necessary to accomplish these changes. This could be
   altering the existing chart, adding new Azure or Kubernetes
   resources, or anything, really.

7. Once you are done, you can destroy all of the resources, and the
   stack:

   ```bash
   $ pulumi destroy
   $ pulumi stack rm
   $ rm kubeconfig.yaml
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [cluster.py](/assets/cluster.py)
- [config.py](/assets/config.py)
- [requirements.txt](/assets/requirements.txt)

