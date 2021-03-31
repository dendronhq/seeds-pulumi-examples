---
id: aws-ts-url-shortener-cache-http
title: Aws Ts URL Shortener Cache HTTP
desc: ''
updated: 1617203999365
created: 1617203999365
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Serverless URL Shortener with Redis Cache and HttpServer

A sample URL shortener SPA that uses the high-level components. The example shows to combine serverless functions along with containers. This shows that you can create your own higher level
abstractions for your own use, your team's, or to share with the community using your language's package manager.

## Deploying and running the program

Note: some values in this example will be different from run to run.  These values are indicated
with `***`.

1. Create a new stack:

   ```
   $ pulumi stack init url-cache-testing
   ```

2. Configure Pulumi to use an AWS region that supports Fargate, which is currently only available in `us-east-1`, `us-east-2`, `us-west-2`, and `eu-west-1`:

   ```
   $ pulumi config set aws:region us-west-2
   ```

3. Set a value for the Redis password. The value can be an encrypted secret, specified with the `--secret` flag. If this flag is not provided, the value will be saved as plaintext in `Pulumi.url-cache-testing.yaml` (since `url-cache-testing` is the current stack name).

   ```
   $ pulumi config set --secret redisPassword S3cr37Password
   ```

4. Add the 'www' directory to the uploaded function code so it can be served from the http server:

   ```
   $ pulumi config set cloud-aws:functionIncludePaths www
   ```

5. Restore NPM modules via `npm install` or `yarn install`.

6. Compile the program via `tsc` or `npm run build` or `yarn run build`.

7. Preview and run the deployment via `pulumi update`. The operation will take about 5 minutes to complete.

   ```
   $ pulumi update
   Previewing stack 'url-cache-testing'
   ...

   Updating stack 'url-cache-testing'
   Performing changes:

   #:  Resource Type                            Name
   1:  pulumi:pulumi:Stack                      url-shortener-cache-url-
   ...
   49: aws:apigateway:Stage                     urlshortener

   info: 49 changes performed:
       + 49 resources created
   Update duration: ***
   ```

8. To view the API endpoint, use the `stack output` command:

   ```
   $ pulumi stack output endpointUrl
   https://***.us-east-1.amazonaws.com/stage/
   ```

9. Open this page in a browser and you'll see a single page app for creating and viewing short URLs.

## Clean up

To clean up resources, run `pulumi destroy` and answer the confirmation question at the prompt.

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [cache.ts](/assets/cache.ts)
- [config.ts](/assets/config.ts)
- [index.ts](/assets/index.ts)
- [package.json](/assets/package.json)
- [tsconfig.json](/assets/tsconfig.json)

