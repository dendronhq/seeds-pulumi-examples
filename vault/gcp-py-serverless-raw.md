---
id: gcp-py-serverless-raw
title: Gcp Py Serverless Raw
desc: ''
updated: 1617203999531
created: 1617203999531
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Google Cloud Functions in Python and Go deployed

This example deploys two Google Cloud Functions. "Hello World" functions are implemented in Python and Go. Pulumi program is implemented in Python.

```bash
# Create and configure a new stack
$ pulumi stack init testing
$ pulumi config set gcp:project <your-gcp-project>
$ pulumi config set gcp:region <gcp-region>

# Preview and run the deployment
$ pulumi up
Previewing changes:
...
Performing changes:
...
info: 6 changes performed:
    + 6 resources created
Update duration: 1m14s

# Test it out
$ curl $(pulumi stack output python_endpoint)
"Hello World!"
$ curl $(pulumi stack output go_endpoint)
"Hello World!"

# Remove the app
$ pulumi destroy
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [requirements.txt](/assets/requirements.txt)

