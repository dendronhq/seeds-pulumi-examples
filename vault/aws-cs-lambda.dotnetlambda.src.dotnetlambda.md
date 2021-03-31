---
id: aws-cs-lambda.dotnetlambda.src.dotnetlambda
title: Dotnetlambda
desc: ''
updated: 1617203999948
created: 1617203999948
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# AWS Lambda Starter Function

This starter function takes a string input, and returns the `toUpper` of it.

This project must be published prior to running `pulumi up` so that our pulumi program can create an [Archive](https://www.pulumi.com/docs/reference/pkg/nodejs/pulumi/pulumi/asset/#Archive).

```bash
dotnet publish
```

See the [AWS .NET Lambda documentation](https://aws.amazon.com/blogs/compute/developing-net-core-aws-lambda-functions/) for more. 

## About

Generated with: 

```sh
dotnet new lambda.EmptyFunction
```

See the [AWS .NET Lambda documentation](https://aws.amazon.com/blogs/compute/developing-net-core-aws-lambda-functions/) for more C# templates. 

* * *

## Imported Assets

- [DotnetLambda.csproj](/assets/dotnetlambda.csproj)
- [Function.cs](/assets/function.cs)

