---
id: aws-ts-eks-migrate-nodegroups
title: Aws Ts Eks Migrate Nodegroups
desc: ''
updated: 1617203999325
created: 1617203999325
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# Zero Downtime Migration of EKS Node Groups

Creates an EKS cluster with node groups and a workload, and showcases adding a
node group to use for workload migration with zero downtime.

For step-by-step instructions, check out the [tutorial][tutorial-migrate-nodegroups].

[tutorial-migrate-nodegroups]: https://www.pulumi.com/docs/tutorials/kubernetes/eks-migrate-nodegroups/

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [echoserver.ts](/assets/echoserver.ts)
- [iam.ts](/assets/iam.ts)
- [index.ts](/assets/index.ts)
- [nginx-ing-cntlr-rbac.ts](/assets/nginx-ing-cntlr-rbac.ts)
- [nginx-ing-cntlr.ts](/assets/nginx-ing-cntlr.ts)
- [nginx.ts](/assets/nginx.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)
- [utils.ts](/assets/utils.ts)

