---
id: aws-ts-airflow
title: Aws Ts Airflow
desc: ''
updated: 1617203999308
created: 1617203999308
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# RDS Postgres and Containerized Airflow

A Pulumi program to deploy an RDS Postgres instance and containerized Airflow.

## Deploying and running the program

For more information on how to run this example, see: <https://www.pulumi.com/docs/> and <https://www.pulumi.com/docs/get-started/>

1. Create a new stack:

   ```bash
   $ pulumi stack init airflow
   ```

2. Set the AWS region:

   ```
   $ pulumi config set aws:region us-east-1
   ```

3. Set the desired RDS password with:

   ```
   $ pulumi config set --secret airflow:dbPassword DESIREDPASSWORD
   ```

4. Restore NPM modules via `yarn install`.

5. Run `pulumi up` to preview and deploy changes.  After the preview is shown you will be
   prompted if you want to continue or not.

```
Previewing update of stack 'airflow'
Previewing changes:

     Type                                           Name                              Plan       Info
 +   pulumi:pulumi:Stack                            airflow                           create
...
```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

