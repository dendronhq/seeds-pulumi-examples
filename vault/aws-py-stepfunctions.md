---
id: aws-py-stepfunctions
title: Aws Py Stepfunctions
desc: ''
updated: 1617203999301
created: 1617203999301
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# AWS Step Functions

A basic example that demonstrates using AWS Step Functions with a Lambda function, written in Python.

```bash
# Create and configure a new stack
pulumi stack init stepfunctions-dev
pulumi config set aws:region us-east-2

# Preview and run the deployment
pulumi up

# Start execution using the AWS CLI (or from the console at https://console.aws.amazon.com/states)
aws stepfunctions start-execution --state-machine-arn $(pulumi stack output state_machine_arn)

# Remove the app and its stack
pulumi destroy && pulumi stack rm -y
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [iam.py](/assets/iam.py)
- [requirements.txt](/assets/requirements.txt)

