---
id: aws-cs-eks
title: Aws Cs Eks
desc: ''
updated: 1617203999239
created: 1617203999239
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# AWS C# EKS Cluster

This example creates an AWS EKS Cluster and deploys a sample container application to it

## Deploying the App

 To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Install DotNet SDK](https://docs.microsoft.com/en-us/dotnet/core/install/sdk?pivots=os-windows)
3. [Configure AWS Credentials](https://www.pulumi.com/docs/intro/cloud-providers/aws/setup/)
4. [Install `aws-iam-authenticator`](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)
5. [Install `kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

### Steps

After cloning this repo, run these commands from the working directory:

1. Create a new stack, which is an isolated deployment target for this example:

   ```bash
   $ pulumi stack init dev
   ```

2. Set your desired AWS region:

   ```bash
   $ pulumi config set aws:region us-east-1 # any valid AWS region will work
   ```

3. Execute the Pulumi program to create our EKS Cluster:

   ```bash
   pulumi up
   ```

4. After 10-15 minutes, your cluster will be ready, and the kubeconfig JSON you'll use to connect to the cluster will
   be available as an output. You can save this kubeconfig to a file like so:

   ```bash
   $ pulumi stack output kubeconfig --show-secrets >kubeconfig.json
   ```

    Once you have this file in hand, you can interact with your new cluster as usual via `kubectl`:

   ```bash
   $ KUBECONFIG=./kubeconfig.json kubectl get nodes
   ```

5. Ensure that the application is running as expected:

   ```bash
   $ curl $(pulumi stack output Url) 
   ```


7. Afterwards, destroy your stack and remove it:

   ```bash
   pulumi destroy --yes
   pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [Aws.EksCluster.csproj](/assets/aws.csproj)
- [EksStack.cs](/assets/eksstack.cs)
- [Program.cs](/assets/program.cs)
- [Pulumi.yaml](/assets/pulumi.yaml)

