---
id: aws-py-appsync
title: Aws Py Appsync
desc: ''
updated: 1617203999287
created: 1617203999287
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# GraphQL Endpoint in AWS AppSync

This example shows how to setup a basic GraphQL endpoint in AWS AppSync. The endpoint contains one query and one mutation that get and put items to a Dynamo DB table.

## Deploying and running the Pulumi App

1. Create a new stack:

   ```bash
   $ pulumi stack init dev
   ```

2. Set the AWS region:

   ```bash
   $ pulumi config set aws:region us-east-2
   ```

3. Run `pulumi up` to preview and deploy changes:

   ```bash
   $ pulumi up
   Previewing update (dev):
   ...

   Updating (dev):
   ...
   Resources:
       + 10 created
   Duration: 20s
   ```

4. Check the deployed GraphQL endpoint:

   ```bash
   $ pulumi stack output endpoint
   https://***.appsync-api.us-east-2.amazonaws.com/graphql
   $ pulumi stack output key
   ***sensitivekey***
   $ curl -XPOST -H "Content-Type:application/graphql" -H "x-api-key:$(pulumi stack output key)" -d '{ "query": "mutation AddTenant { addTenant(id: \"123\", name: \"FirstCorp\") { id name } }" }' "$(pulumi stack output endpoint)" 
   {
       "data": {
           "addTenant": {
               "id": "123",
               "name": "FirstCorp"
           }
       }
   }
   ```

## Clean up

1. Run `pulumi destroy` to tear down all resources.

2. To delete the stack itself, run `pulumi stack rm`. Note that this command deletes all deployment history from the Pulumi Console.

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

