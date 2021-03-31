---
id: aws-py-resources
title: Aws Py Resources
desc: ''
updated: 1617203999296
created: 1617203999296
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# AWS Resources

A Pulumi program that demonstrates creating various AWS resources in Python

```bash
# Create and configure a new stack
$ pulumi stack init dev
$ pulumi config set aws:region us-east-2

# Preview and run the deployment
$ pulumi up

# Remove the app
$ pulumi destroy
$ pulumi stack rm
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

