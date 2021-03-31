---
id: aws-go-console-slack-notification
title: Aws Go Console Slack Notification
desc: ''
updated: 1617203999254
created: 1617203999254
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# AWS Console Change Slack Notifier in Go

This example deploys a Lambda function and relevant CloudTrail and CloudWatch resources to send a 
Slack notification for any resource operation that is performed via the AWS Console.

Note: This application sets up the necessary infrastructure across _each_ AWS region in your 
account that is `opt-in-not-required` or `opted-in`. The Pulumi application uses the 
[DescribeRegions](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeRegions.html) API
via [aws-sdk-go](https://github.com/aws/aws-sdk-go) to query for available regions.

## Deploying the App

 To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Configure AWS Credentials](https://www.pulumi.com/docs/intro/cloud-providers/aws/setup/)

### Steps

After cloning this repo, run these commands from the working directory:

1. Build the handler:

   - For developers on Linux and macOS:

     ```bash
     make
     ```
   - For developers on Windows:

     - Get the `build-lambda-zip` tool:

       ```bash
       set GO111MODULE=on
       go.exe get -u github.com/aws/aws-lambda-go/cmd/build-lambda-zip
       ```

     - Use the tool from your GOPATH:
       ```bash
       set GOOS=linux
       set GOARCH=amd64
       set CGO_ENABLED=0
       go build -o handler\dist\handler handler\handler.go
       %USERPROFILE%\Go\bin\build-lambda-zip.exe -o handler\dist\handler.zip handler\dist\handler
       ```

2. Create a new Pulumi stack, which is an isolated deployment target for this example:

   ```bash
   pulumi stack init
   ```

3. Set the required configuration variables for this program:

   ```bash
   pulumi config set slackWebhookURL 'YOUR_SLACK_WEBHOOK_URL'
   ```

4. Execute the Pulumi program to create our lambda:

   ```bash
   pulumi up
   ```

5. Perform a change in the AWS Console and look for a notification in your Slack channel. Note: you 
   must perform a _write_ such as adding or removing tags from a resource, launching an instance, or 
   deleting a resource.

6. From there, feel free to experiment. Simply making edits, rebuilding your handler, and running 
   `pulumi up` will update your lambda. Customize the Slack message username or text with the following 
   configuration values:

   ````
   ```bash
   pulumi config set slackMessageUsername 'Console Change Monitor'
   pulumi config set slackMessageText ':warning: Somebody made a change in the console!'
   ```
   ````

7. Afterwards, destroy your stack and remove it:

   ```bash
   pulumi destroy --yes
   pulumi stack rm --yes
   ```

* * *

## Imported Assets

- [Makefile](/assets/makefile)
- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)

