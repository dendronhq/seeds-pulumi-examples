---
id: gcp-go-instance
title: Gcp Go Instance
desc: ''
updated: 1617203999518
created: 1617203999518
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# GCP Instance

Create a GCP instance using Pulumi + Go.

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init gcp-instance
   ```

2. Configure the project:

   ```
   $ pulumi config set gcp:project YOURGOOGLECLOUDPROJECT
   $ pulumi config set gcp:zone us-central1-a
   ```

3. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing update (gcp-instance):
   ...

   Updating (gcp-instance):
       Type                     Name       Status      
   +   pulumi:pulumi:Stack      gcp-instance  created     
   +   └─ gcp:compute:Instance  instance   created     

   Outputs:
       instanceName: "instance-6beb431"

   Resources:
       + 2 created

   Duration: 23s
   ```

4. Cleanup

   ```
   $ pulumi destroy
   $ pulumi stack rm
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

