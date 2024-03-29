---
id: aws-py-ec2-provisioners
title: Aws Py Ec2 Provisioners
desc: ''
updated: 1617203999290
created: 1617203999290
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# AWS WebServer with Manual Provisioning (in Python)

This demonstrates using Pulumi dynamic providers to accomplish post-provisioning configuration steps.

Using these building blocks, one can accomplish much of the same as Terraform provisioners.

<https://github.com/pulumi/pulumi/issues/1691> tracks designing and developing a complete replacement for provisioners.

## Running the Example

First, create a stack, using `pulumi stack init`.

Next, generate an OpenSSH keypair for use with your server - as per the AWS [Requirements][1]

```
$ ssh-keygen -t rsa -f rsa -b 4096 -m PEM
```

This will output two files, `rsa` and `rsa.pub`, in the current directory. Be sure not to commit these files!

We then need to configure our stack so that the public key is used by our EC2 instance, and the private key used
for subsequent SCP and SSH steps that will configure our server after it is stood up.

```
$ cat rsa.pub | pulumi config set publicKey --
$ cat rsa | pulumi config set privateKey --secret --
```

If your key is protected by a passphrase, add that too:

```
$ pulumi config set privateKeyPassphrase --secret [yourPassphraseHere]
```

Notice that we've used `--secret` for both `privateKey` and `privateKeyPassphrase`. This ensures their are
stored in encrypted form in the Pulumi secrets system.

Also set your desired AWS region:

```
$ pulumi config set aws:region us-west-2
```

From there, you can run `pulumi up` and all resources will be provisioned and configured.

[1]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#how-to-generate-your-own-key-and-import-it-to-aws

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [myapp.conf](/assets/myapp.conf)
- [provisioners.py](/assets/provisioners.py)
- [requirements.txt](/assets/requirements.txt)

