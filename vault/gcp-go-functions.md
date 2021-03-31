---
id: gcp-go-functions
title: Gcp Go Functions
desc: ''
updated: 1617203999513
created: 1617203999513
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Google Cloud Functions in Python deployed with Go

This example deploys a Google Cloud Function implemented in Go. Pulumi program is also implemented in Go.

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Configure Pulumi for GCP](https://www.pulumi.com/docs/intro/cloud-providers/gcp/setup/)
   - [Set up a Service Account](https://www.pulumi.com/docs/intro/cloud-providers/gcp/service-account/)

### Steps

1. Create a new stack:

   ```
   $ pulumi stack init dev
   ```

2. Set the GCP project and region:

   ```bash
   pulumi config set gcp:project <gcp-project>
   pulumi config set gcp:region <gcp-region>
   ```

3. Execute the pulumi program to deploy our function:

   ```bash
   pulumi up
   ```

4. Test our function by curl-ing the trigger URL.

   ```bash
   curl $(pulumi stack output function)
   # "Hello World!"
   ```

5. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your function.

6. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

   ```bash
   pulumi destroy --yes
   pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

