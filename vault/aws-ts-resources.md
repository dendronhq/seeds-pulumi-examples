---
id: aws-ts-resources
title: Aws Ts Resources
desc: ''
updated: 1617203999341
created: 1617203999341
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# AWS Resources

A Pulumi program that demonstrates creating various AWS resources.

```bash
# Create and configure a new stack
$ pulumi stack init aws-resources-dev
$ pulumi config set aws:region us-east-2

# Install dependencies
$ npm install

# Preview and run the deployment
$ pulumi up

# Remove the app
$ pulumi destroy
$ pulumi stack rm
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

