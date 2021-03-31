---
id: aws-ts-stepfunctions
title: Aws Ts Stepfunctions
desc: ''
updated: 1617203999356
created: 1617203999356
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# AWS Step Functions

A basic example that demonstrates using AWS Step Functions with a Lambda function.

```
# Create and configure a new stack
$ pulumi stack init stepfunctions-dev
$ pulumi config set aws:region us-east-2

# Install dependencies
$ npm install

# Preview and run the deployment
$ pulumi up

# Start execution using the AWS CLI (or from the console at https://console.aws.amazon.com/states)
$ aws stepfunctions start-execution --state-machine-arn $(pulumi stack output stateMachineArn)

# Remove the app
$ pulumi destroy
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

