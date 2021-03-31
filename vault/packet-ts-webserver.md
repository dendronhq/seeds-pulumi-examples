---
id: packet-ts-webserver
title: Packet Ts Webserver
desc: ''
updated: 1617203999579
created: 1617203999579
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Packet Webserver

This example demonstrates creating a webserver in Packet.net

# Running the Example

After cloning this repo, `cd` into it and run these commands.

1. Create a new stack, which is an isolated deployment target for this example:

   ```bash
   $ pulumi stack init
   ```

2. Install all of the dependencies for the application:

   ```bash
   $ npm install
   ```

3. Deploy everything with the `pulumi up` command. This provisions the webserver:

   ```bash
   $ pulumi up
   ```

4. After a couple minutes, your webserver will be ready.

   ```bash
   $ pulumi up
   ...

   Outputs:
     + ip  : "147.75.65.213"
     + name: "new-vervet"
   ```

5. Once you are done, you can destroy all of the resources, and the stack:

   ```bash
   $ pulumi destroy
   $ pulumi stack rm
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

