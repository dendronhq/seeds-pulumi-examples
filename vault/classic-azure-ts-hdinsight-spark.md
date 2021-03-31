---
id: classic-azure-ts-hdinsight-spark
title: Classic Azure Ts Hdinsight Spark
desc: ''
updated: 1617203999467
created: 1617203999467
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Spark on Azure HDInsight

An example Pulumi component that deploys a Spark cluster on Azure HDInsight.

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

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:
   ...
   info: 5 changes performed:
       + 5 resources created
   Update duration: 15m6s
   ```

5. Check the deployed Spark endpoint:

   ```
   $ pulumi stack output endpoint
   https://myspark1234abcd.azurehdinsight.net/

   # For instance, Jupyter notebooks are available at https://myspark1234abcd.azurehdinsight.net/jupyter/
   # Follow https://docs.microsoft.com/en-us/azure/hdinsight/spark/apache-spark-load-data-run-query to test it out
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

