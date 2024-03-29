---
id: gcp-go-webserver
title: Gcp Go Webserver
desc: ''
updated: 1617203999520
created: 1617203999520
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Web Server Using Compute Engine

Starting point for building the Pulumi web server sample in Google Cloud.

## Running the App

1. Create a new stack:

   ```
   $ pulumi stack init webserver-gcp-testing
   ```

2. Configure the project:

   ```
   $ pulumi config set gcp:project YOURGOOGLECLOUDPROJECT
   $ pulumi config set gcp:zone us-central1-a
   ```

3. Restore NPM dependencies:

   ```
   $ npm install
   ```

4. Run `pulumi up` to preview and deploy changes:

   ```
   $ pulumi up
   Previewing changes:
   ...

   Performing changes:

       Type                     Name                                 Status      Info
   +   pulumi:pulumi:Stack      webserver-gcp-webserver-gcp-testing  created
   +   ├─ gcp:compute:Network   network                              created
   +   ├─ gcp:compute:Firewall  firewall                             created
   +   └─ gcp:compute:Instance  instance                             created

   ---outputs:---
   instanceIP  : "35.185.200.158"
   instanceName: "instance-af7e53b"

   info: 4 changes performed:
       + 4 resources created
   Update duration: 1m23s
   ```

5. Curl the HTTP server:

   ```
   $ curl $(pulumi stack output instanceIP)
   Hello, World!
   ```

6. SSH into the server:

   ```
   $ gcloud compute ssh $(pulumi stack output instanceName)
   Warning: Permanently added 'compute.4281826686797606751' (ECDSA) to the list of known hosts.

   The programs included with the Debian GNU/Linux system are free software;
   the exact distribution terms for each program are described in the
   individual files in /usr/share/doc/*/copyright.

   Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
   permitted by applicable law.
   albert@instance-af7e53b:~$
   ```

7. Cleanup

   ```
   $ pulumi destroy
   $ pulumi stack rm
   ```

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

